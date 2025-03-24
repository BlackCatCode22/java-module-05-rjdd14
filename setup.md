
## 1. Introduction / Overview

Hey, so here’s what I’m working on for the midterm project "Zookeeper’s Challenge." Essentially, my goal is to simulate how a zoo handles its animals by reading data from a couple of text files and using the provided Java classes to manage everything.
  I need to mimic zoo animal management. I'll be reading in data from `arrivingAnimals.txt` (for animal details) and `animalNames.txt` (for names) and then using classes like `Animal.java`, `Hyena.java`, and others to handle the information.

  My project will:
  - Read and process animal data.
  - Create and manage animal objects.
  - Demonstrate object-oriented design using the given files.
  - Serve as a practice run for the midterm by focusing on design, planning, and code review.

## 2. Overview of Provided Files

Here are the files, along with what I think each one does:

- **Animal.java:**  
  This is likely the base class for all animal objects. It probably includes basic properties (like species, age, etc.) and common methods.

- **AnimalNameListsWrapper.java:**  
  This class wraps up the list of animal names from the `animalNames.txt` file. It’s probably used to easily manage and access the names in the program.

- **animalNames.txt:**  
  A simple text file containing a list of animal names. These names might be used to assign or validate animal names in my objects.

- **App.java:**  
  The main driver of the application. This file should contain the `main` method that ties everything together.

- **arrivingAnimals.txt:**  
  Another text file with details on the animals arriving at the zoo. I’ll need to parse this file and convert the data into animal objects.

- **Utilities.java:**  
  Contains helper methods for common tasks like file reading and data parsing. This should make the process of handling files and data smoother.


## 3. Functional Requirements

Here’s what my program needs to do:

- **Data Input:**  
  - Read animal details from `arrivingAnimals.txt`.
  - Read and manage animal names from `animalNames.txt` using `AnimalNameListsWrapper.java`.

- **Animal Management:**  
  - Instantiate animal objects from `Animal.java` and its subclass `Hyena.java`.
  - Organize these objects using data structures that allow me to add, remove, or update them as needed.

- **System Integration:**  
  - Use `App.java` to coordinate the overall application flow.
  - Rely on `Utilities.java` for supporting functions like file I/O and data parsing.


## 4. System Architecture & Data Flow

I’m picturing the project like this:

1. **File Input:**  
   I’ll use utility functions to read the two text files (`arrivingAnimals.txt` and `animalNames.txt`).

2. **Data Parsing & Object Creation:**  
   The raw data from the files will be parsed and turned into objects (instances of `Animal`, `Hyena`, etc.). The `AnimalNameListsWrapper.java` will help manage the list of names.

3. **Data Storage:**  
   I plan to use data structures like an ArrayList (to preserve the order of arrival) and a HashMap (for fast lookup by name or ID).

4. **Application Logic:**  
   The main logic in `App.java` will handle everything – reading files, processing data, and managing user interactions (if any). Utilities from `Utilities.java` will support these tasks.


## 5. Design Decisions & Data Structures

I’ve been thinking about which data structures work best:

- **ArrayList:**  
  Perfect for keeping the order of animals as they arrive. It’s simple and effective for iteration and adding new items.

- **HashMap:**  
  Great for mapping animal names or IDs to their objects. This makes it super fast to find a particular animal.

- **Other Options:**  
  I might consider a Queue or LinkedList if I end up needing to manage a waiting list or similar ordered operations.


```java
// Example: Reading animal names from a file
import java.io.*;
import java.util.ArrayList;

public class AnimalLoader {
    public static ArrayList<String> loadAnimalNames(String filename) {
        ArrayList<String> animalNames = new ArrayList<>();
        try (BufferedReader br = new BufferedReader(new FileReader(filename))) {
            String name;
            while ((name = br.readLine()) != null) {
                animalNames.add(name);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
        return animalNames;
    }
    
    public static void main(String[] args) {
        ArrayList<String> names = loadAnimalNames("animalNames.txt");
        System.out.println("Loaded animal names: " + names);
    }
}