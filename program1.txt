def StdInput():
    pass
    names = []
    n = int(input("Enter the number of names to be reversed: "))
    for i in range(n):
        org = input("Enter a name: ")
        rev = org[::-1]
        names.append(rev)
    print("Reversed names:")
    for name in names:
        print(name)


def FileInput():
    pass
    fname = input("Enter the input file name: ")
    try:
        with open(fname,'r') as f:
            names = f.read()
    except FileNotFoundError:
        print("File not found.")
    reversed_file = input("Enter the output file name: ")
    reverse_contents=names[::-1]
    with open(reversed_file, 'w') as rf:
        rf.write(reverse_contents)
    print("file created")
    print(" the reversed names are written to "+reversed_file)


while True:
    print("********")
    print("1. Accept Input from Standard Input Device")
    print("2. Accept Input from File")
    print("3. Exit")
    print("********")
    print("Please enter your choice:")
    choice = int(input())
    if choice == 1:
        StdInput()
    elif choice == 2:
        FileInput()
    elif choice == 3:
        print("You chose exit!")
        exit(0)
    else:
        print("invalid choice!")
