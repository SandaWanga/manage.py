# manage.py
make a copy of your previous Capstone project (task_manager.py)
#=====importing libraries===========
'''This is the section where you will import libraries'''
from datetime import datetime,date
import datetime


#====Login Section====
'''Here you will write code that will allow a user to login.
    - Your code must read usernames and password from the user.txt file
    - You can use a list or dictionary to store a list of usernames and passwords from the file.
    - Use a while loop to validate your user name and password.
'''
logins = []
# Declaring functions
def reg_user():

            # Get all usernames 
            for line in open("user.txt","r").readlines(): 
                user,_= line.split(", ") 

            # Get a new username and check if it exists
            new_username = input("Enter new Username :")  
            while new_username == user:
             
              print(new_username + " already exists!\n")
              new_username = input("Enter new Username :") 

              
        # If the new username is not already listed, it is added to usernames_list
            if new_username != user:
                new_password = input("Enter new Password :")
                pass_confirm = input("Please confirm your new password: \n")
                
           # The user will then be prompted to enter a password     
                while new_password != pass_confirm:

           #  User is asked to confirm their new password
                    print("Your confimed password does not match the original password.")
                    new_password = input("Please enter your new password: \n")

                 # User is prompted to enter their new password and confirm it until they match
                    pass_confirm = input("Please confirm your new password: \n")
                    if new_password == pass_confirm:
                        print("Your password is valid.")
                                
                file = open("user.txt","a")
                file.write("\n")
                file.write(new_username)
                file.write(", ")
                file.write(new_password)
                file.close()
            print("Username " + new_username + " has been created\n" )
                        

def add_task():
    
     
    # Getting user input on the username of the person the task is assigned to.
    username= input("Enter your Username of the person the task is assigned to :")
        
        # Getting user input on the title of the task being added. 
    title_of_the_task= (input("Enter your job title: "))
        
        # Getting information regarding the description of the added task.
    description=input("Enter job discription: ")

            # Using the previously imported datetime module today() function to calculate the current date.
    current_date = datetime.date.today()

            # Changing the date object to a string in the correct date format.
    assigned_date = current_date.strftime('%d %b %Y')

            # Getting input on the due date of the task being added.
    date_format = input("Please enter the due date of the task (e.g. dd-mm-yyyy): \n")

    date_list = date_format.split("-")

    numbers_date = [int(x) for x in date_list]

    due_date = date(numbers_date[2], numbers_date[1], numbers_date[0]).strftime('%d %b %Y') 

    
    file = open("tasks.txt","a")
    file.write("\n")
    file.write(username +", " + title_of_the_task + ", " + 
                    description + ", " + str(current_date) + ", " + str(due_date) +", No" )
    bad_chars = ["[", "]", "\'",]  
    for i in bad_chars:  

        

     print("Task  has been created " )

def view_all():
    file = open("tasks.txt","r")
    print(file.read())
    print('\n')
          
    file.close()


def view_mine():
    
  file = open("tasks.txt", "r")
  for line in file:
     if line != "n":
        line = line.split(",")
        line[-1] = line[-1].strip()
        if line[0] == username:
          print( line[0],"," , line[1],",",line[2],",",line[3], ",", line[4],",", line[5] )

  file.close()


with open("user.txt", "r") as f:
    for line in f.readlines():
        user, passw = line.split(", ")
        logins.append((user.strip(), passw.strip()))

while True:
  username = input("Enter your Username :")
  password = input("Enter your Password :")
  if (username, password) in logins:
        print("Welcome\n")
        break
  else:
    print("Incorrect username or password", "Please try again", sep='\n')     
    continue
  
while True:
    #presenting the menu to the user and 
    # making sure that the user input is coneverted to lower case.
    menu = input('''Select one of the following Options below:
r - Registering a user
a - Adding a task
va - View all tasks
vm - view my task
gr - Generate reports 
ds - Display staticks 
e - Exit
: ''').lower()
    
    if username == "admin" and menu == "r":

        # Calling register function
        reg_user()

    elif menu == "a":

        # Calling add task function
        add_task()

    elif menu == "va":

         # Calling view all function
        view_all()

    elif menu == "vm":
        
    # Calling view mine function
         view_mine()

    elif menu == "gr":
        task_overview = open("task_overview.txt", "w")
        user_overview = open("user_overview.txt", "w")
        file_overview = open("tasks.txt", "r")
        numOf_tasks = 0
        for tasks in file_overview:
            uncompleted_tasks = 0
        completed =0
        if completed == "no":
            uncompleted_tasks += 1
            completed_tasks = 0
            if completed == "yes":
                completed_tasks += 1



    elif menu == 'e':
        print('Goodbye!!!')
        exit()

    else:
        print("You are not allowed to register users \n")
        
else:
    print("You have made a wrong choice, Please Try again")

    
    
         

   

