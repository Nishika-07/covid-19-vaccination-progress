# Import necessary libraries
from datetime import datetime

# Class to represent a person
class Person:
    def __init__(self, name, age, is_essential_worker, has_preexisting_condition):
        self.name = name
        self.age = age
        self.is_essential_worker = is_essential_worker
        self.has_preexisting_condition = has_preexisting_condition
        self.is_vaccinated = False
        self.vaccination_date = None

    # Determine eligibility based on age, occupation, and health
    def is_eligible(self):
        return self.age >= 65 or self.is_essential_worker or self.has_preexisting_condition

    # Administer the vaccine
    def administer_vaccine(self):
        if self.is_eligible():
            self.is_vaccinated = True
            self.vaccination_date = datetime.now().strftime("%Y-%m-%d")
            print(f"{self.name} has been vaccinated on {self.vaccination_date}.")
        else:
            print(f"{self.name} is not eligible for vaccination at this time.")

# Function to simulate the vaccination process
def vaccination_process(people):
    for person in people:
        print(f"Processing {person.name}...")
        if person.is_eligible():
            person.administer_vaccine()
        else:
            print(f"{person.name} is not eligible for vaccination.\n")

# Example usage
if __name__ == "__main__":
    # Create a list of people to vaccinate
    people = [
        Person(name="Alice", age=70, is_essential_worker=False, has_preexisting_condition=False),
        Person(name="Bob", age=45, is_essential_worker=True, has_preexisting_condition=True),
        Person(name="Charlie", age=30, is_essential_worker=False, has_preexisting_condition=False),
        Person(name="Diana", age=55, is_essential_worker=True, has_preexisting_condition=False)
    ]

    # Run the vaccination process
    vaccination_process(people)
