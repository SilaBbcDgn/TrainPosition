import random

# Constants for track circuits
TRACK_CIRCUIT_1_RANGE = (1, 50)
TRACK_CIRCUIT_2_RANGE = (51, 100)

# Function to calculate the train's position
def where_is_train():
    train_len = 10  # Length of the train
    train_center = random.randint(10, 100)  # Random central position of the train
    start_point = max(0, train_center - train_len)  # Calculate start position
    end_point = start_point + train_len  # Calculate end position
    print(f"Train center position: {train_center}")
    print(f"Train start position: {start_point}, Train end position: {end_point}")
    return start_point, end_point, train_len

# Function to check which track circuits are occupied
def track_circuits(start_point, end_point):
    # Check for overlap with Track Circuit 1
    is_track_circuit_1_occupied = (
        start_point <= TRACK_CIRCUIT_1_RANGE[1]
        and end_point >= TRACK_CIRCUIT_1_RANGE[0]
    )

    # Check for overlap with Track Circuit 2
    is_track_circuit_2_occupied = (
        start_point <= TRACK_CIRCUIT_2_RANGE[1]
        and end_point >= TRACK_CIRCUIT_2_RANGE[0]
    )

    # Determine occupied circuits
    occupied_circuits = []
    if is_track_circuit_1_occupied:
        occupied_circuits.append("Track Circuit 1")
    if is_track_circuit_2_occupied:
        occupied_circuits.append("Track Circuit 2")

    # Print results
    if occupied_circuits:
        print(f"Occupied circuits: {', '.join(occupied_circuits)}")
    else:
        print("No track circuit is occupied")

    return occupied_circuits

# Function calls
start_point, end_point, train_len = where_is_train()
occupied_circuits = track_circuits(start_point, end_point)

print(f"Final result: Occupied Circuit(s): {', '.join(occupied_circuits) if occupied_circuits else 'None'}")
