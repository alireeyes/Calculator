    import math
    import statistics

    def advanced_calculator(data):
    """
    Advanced calculator function with operations on a list of numbers.
    """
    if not data or not isinstance(data, list):
        raise ValueError("Input data must be a non-empty list of numbers.")

    results = {}

    # Addition
    results['add'] = sum(data)

    # Subtraction
    subtract_result = data[0]
    for num in data[1:]:
        subtract_result -= num
    results['subtract'] = subtract_result

    # Multiplication
    multiply_result = 1
    for num in data:
        multiply_result *= num
    results['multiply'] = multiply_result

    # Division
    divide_result = data[0]
    try:
        for num in data[1:]:
            divide_result /= num
        results['divide'] = divide_result
    except ZeroDivisionError:
        results['divide'] = "Division by zero is undefined."

    # Power
    try:
        power_result = data[0]
        for num in data[1:]:
            if abs(power_result) > 1e10 or abs(num) > 1e5:  # Check for large values
                raise OverflowError("Power calculation too large.")
            power_result = math.pow(power_result, num)
        results['power'] = power_result
    except OverflowError:
        results['power'] = "OverflowError: Power calculation exceeded range."

    # Square root
    results['sqrt'] = [math.sqrt(num) for num in data if num >= 0]

    # Statistical calculations
    if len(data) > 1:
        results['mean'] = statistics.mean(data)
        results['median'] = statistics.median(data)
        results['variance'] = statistics.variance(data)
        results['standard_deviation'] = statistics.stdev(data)
    else:
        results['mean'] = data[0]
        results['median'] = data[0]
        results['variance'] = "Variance requires at least two data points."
        results['standard_deviation'] = "Standard deviation requires at least two data points."

    return results

    # Main interactive script
    if __name__ == "__main__":
    print("Welcome to the Advanced Calculator!")
    
    while True:
        # Display available operations
        print("\nAvailable operations:")
        print("1. Add")
        print("2. Subtract")
        print("3. Multiply")
        print("4. Divide")
        print("5. Power")
        print("6. Square Root")
        print("7. Mean")
        print("8. Median")
        print("9. Variance")
        print("10. Standard Deviation")
        print("11. Exit")

        # Get the user's choice
        try:
            choice = int(input("Select an operation (1-11): "))
        except ValueError:
            print("Invalid input. Please enter a number between 1 and 11.")
            continue

        # Exit if the user selects 11
        if choice == 11:
            print("Thank you for using the Advanced Calculator. Goodbye!")
            break

        # Ensure the choice is valid
        if choice < 1 or choice > 11:
            print("Invalid choice. Please select a valid operation.")
            continue

        # Get the numbers from the user
        try:
            data = list(map(float, input("Enter the numbers separated by spaces: ").split()))
        except ValueError:
            print("Invalid input. Please enter valid numbers.")
            continue

        # Perform the chosen operation
        operations = [
            "add", "subtract", "multiply", "divide", "power", "sqrt",
            "mean", "median", "variance", "standard_deviation"
        ]
        operation_name = operations[choice - 1]

        # Perform the calculation
        try:
            result = advanced_calculator(data)
            if operation_name in result:
                print(f"\nResult of {operation_name.capitalize()}: {result[operation_name]}")
            else:
                print(f"\nOperation '{operation_name}' not supported.")
        except Exception as e:
            print(f"An error occurred: {e}")
