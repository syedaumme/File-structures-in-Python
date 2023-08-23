fname = "input2.txt"


class Progthree:



    def pack(self):

        names =[]
        n = int(input("enter no of data to be entered: "))
        for i in range(n):
            name = input("enter name: ")
            usn = input("enter usn: ")
            sem = input("enter sem: ")
            branch = input("enter branch: ")
            b = usn + "|" + name + "|" + sem + "|" + branch + "|"
            names.append(b)

        try:
            with open(fname, 'w') as f:
              for b in names:
                f.write(b+"\n")
        except FileNotFoundError:
            print("invalid file name")

    def unpack(self, fname):
        try:
            with open(fname, 'r') as f:
                for line in f:
                    print("the details are : "+line.strip())

        except FileNotFoundError:
            print("file not found")

    def search(self, fname, k):
        with open(fname, 'r') as f:
            line_number = 0
            for line in f:
                line_number += 1
                if k in line:
                    print("the details are : " + line)
                    print("search successful")

    def modify(self, fname, a, rep):
        with open(fname, 'r') as f:
            lines = f.readlines()

            for i, line in enumerate(lines):

                if a in line:
                    print("the details are : " + line)
                    modified_line = [str(x) for x in rep]
                    lines[i] = "".join(modified_line) + "\n"
                    print("File modified successfully")

        with open(fname, 'w') as f:
            f.writelines(lines)


while True:
    obj = Progthree()
    print("1. Pack")
    print("2. unpack")
    print("3.search")
    print("4.modify")
    print("5. exit")
    ch = input("enter ur choice")
    if ch == "1":
        obj.pack()
    elif ch == "2":
        obj.unpack(fname)
    elif ch == "3":
        k = input("enter the key usn to be searched")
        obj.search(fname, k)
    elif ch == "4":

        a = input("enter the usn to be modified")

        rep = input("enter usn|name|sem|branch")
        obj.modify(fname, a, rep)

    elif ch == "5":
        exit(0)
    else:
        print("INVALID CHOICE!!")



