    # Define a function to add two numbers
    def add(x, y):
    return x + y

    # Define a function to subtract the second number from the first
    def subtract(x, y):
    return x - y

    # Define a function to multiply two numbers
    def multiply(x, y):
    return x * y

    # Define a function to divide the first number by the second
    def divide(x, y):
    return x / y

    # Infinite loop to continuously prompt the user for calculations
    while True:
    # Display the operation menu
    print("Select operation:")
    print("1. Add")
    print("2. Subtract")
    print("3. Multiply")
    print("4. Divide")

    # Prompt the user to select an operation
    choice = input("Enter choice(1/2/3/4): ")

    # Check if the user's choice is valid
    if choice in ('1', '2', '3', '4'):
        # Prompt the user to enter two numbers for the calculation
        num1 = float(input("Enter first number: "))
        num2 = float(input("Enter second number: "))

        # Perform the selected operation and display the result
        if choice == '1':
            print(num1, "+", num2, "=", add(num1, num2))

        elif choice == '2':
            print(num1, "-", num2, "=", subtract(num1, num2))

        elif choice == '3':
            print(num1, "*", num2, "=", multiply(num1, num2))

        elif choice == '4':
            print(num1, "/", num2, "=", divide(num1, num2))
        
        # Ask the user if they want to perform another calculation
        next_calculation = input("Do you want to do another calculation? (yes/no): ")
        if next_calculation.lower() != "yes":
            # Exit the loop if the user doesn't want to continue
            break
    
    else:
        # Display an error message for invalid inputs
        print("Invalid Input")
