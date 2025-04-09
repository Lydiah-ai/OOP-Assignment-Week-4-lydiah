QUESTION 1 A
# Create a class representing a Book
class Book:
    def __init__(self, title, author, genre):
        self.title = Secrets      # Title of the book
        self.author = ProfessorG    # Author of the book
        self.genre = fantacy    # Genre of the book
    
    def describe(self):
        print ("'{self.title}' is a {self.genre} book written by {self.author}.")

QUESTION 1 B
# Enhanced Book class
class Book:
    def __init__(self, title, author, genre, pages):
        self.title = title      # Title of the book
        self.author = author    # Author of the book
        self.genre = genre      # Genre of the book
        self.pages = pages      # Total number of pages
        self.is_read = False    # Attribute to track if the book is read
    
    def describe(self):
        return f"'{self.title}' is a {self.genre} book written by {self.author}, consisting of {self.pages} pages."
    
    def mark_as_read(self):
        self.is_read = True
        return f"You have finished reading '{self.title}'!"
    
    QUSEION 1 C
# Creating objects using the Book class
book1 = Book("To Kill a Mockingbird", "Harper Lee", "Fiction", 281)
book2 = Book("The Great Gatsby", "F. Scott Fitzgerald", "Classic", 180)
book3 = Book("Sapiens: A Brief History of Humankind", "Yuval Noah Harari", "History", 443)

# Testing the methods
print(book1.describe())
print(book2.describe())
print(book3.describe())

# Marking a book as read
print(book1.mark_as_read())

# Checking reading progress
print(book3.reading_progress(150))
print(book3.reading_progress(443))  # Fully read

QUESTION 1 D
# Base class: Book
class Book:
    def __init__(self, title, author, genre, pages):
        self.title = title
        self.author = author
        self.genre = genre
        self.pages = pages
        self.is_read = False  # Encapsulated attribute to track if the book is read

    def describe(self):
        return f"'{self.title}' is a {self.genre} book by {self.author}, consisting of {self.pages} pages."
    
    def mark_as_read(self):
        self.is_read = True
        return f"You have finished reading '{self.title}'!"
    
    def reading_progress(self, current_page):
        if current_page >= self.pages:
            self.is_read = True
            return f"You completed '{self.title}'!"
        else:
            progress = (current_page / self.pages) * 100
            return f"You've read {progress:.1f}% of '{self.title}'. Keep it up!"

# Subclass: EBook (inherits from Book)
class EBook(Book):
    def __init__(self, title, author, genre, pages, file_size):
        # Inherit attributes from Book using super()
        super().__init__(title, author, genre, pages)
        self.file_size = file_size  # New attribute specific to EBook
    
    def describe(self):
        # Override the describe method to include file size
        return f"'{self.title}' (E-Book) by {self.author} - {self.genre}, {self.pages} pages, File size: {self.file_size} MB"
    
    def download(self):
        return f"Downloading '{self.title}'... File size: {self.file_size} MB."

# Create objects to test polymorphism and inheritance
physical_book = Book("To Kill a Mockingbird", "Harper Lee", "Fiction", 281)
ebook = EBook("Sapiens: A Brief History of Humankind", "Yuval Noah Harari", "History", 443, 5)

# Test methods for both base and subclass
print(physical_book.describe())  # From base class
print(ebook.describe())  # Overridden in subclass
print(ebook.download())  # Unique to subclass

# Testing encapsulation
print(physical_book.mark_as_read())
print(ebook.reading_progress(150))

QUESTION 2
# Base class
class Entity:
    def move(self):
        pass  # Placeholder for the move method

# Animal subclasses
class Dog(Entity):
    def move(self):
         print("Running on four legs")

class Fish(Entity):
    def move(self):
        print( "Swimming through water")

# Vehicle subclasses
class Car(Entity):
    def move(self):
        print("Driving on roads ")

# Vehicle subclasses
class Car(Entity):
    def move(self):
        print("Driving on roads ")

class Plane(Entity):
    def move(self):
        print( "Flying in the sky ")

# Testing polymorphism
entities = [Dog(), Fish(), Car(), Plane()]

for entity in entities:
    print(entity.move())
