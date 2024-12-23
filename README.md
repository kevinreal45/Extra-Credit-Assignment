# Airline System

This is an assignment that is meant to display the creation of API for a Simplified Airline Booking System

## Admission Number
`122787`


## Setup Instructions

1. **Clone the repository:**
    ```sh
    git clone <repository_url>
    cd Airline_System
    ```

2. **Create a virtual environment and activate it:**
    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. **Install the dependencies:**
    ```sh
    pip install -r requirements.txt
    ```

4. **Apply migrations:**
    ```sh
    python manage.py migrate
    ```

5. **Run the development server:**
    ```sh
    python manage.py runserver
    ```

6. **Access the API:**
    Open your browser and go to `http://127.0.0.1:8000/api/`

## Models

### Flight
- `flight_number`: CharField, unique
- `departure`: DateTimeField
- `arrival`: DateTimeField
- `origin`: CharField
- `destination`: CharField
- `capacity`: IntegerField

### Passenger
- `first_name`: CharField
- `last_name`: CharField
- `email`: EmailField, unique
- `phone_number`: CharField
- `flight`: ForeignKey to Flight

## Serializers

### _FlightSerializer_
Serializes all fields of the Flight model.

### _PassengerSerializer_
Serializes all fields of the Passenger model and includes a nested FlightSerializer.

## Views/ViewSets

### _FlightViewSet_
- Handles CRUD operations for Flight model.
- Implements pagination.

### _PassengerViewSet_
- Handles CRUD operations for Passenger model.
- Implements pagination.
- Allows filtering passengers by flight number.

## Notable Design Decisions

- **Django Rest Framework**: Used for creating API endpoints with minimal boilerplate.
- **ViewSets**: Simplifies the creation of views by combining the logic for a set of related views in a single class.
- **Pagination**: Implemented to handle large datasets efficiently.
- **Filtering**: Added to allow searching passengers by flight number.
