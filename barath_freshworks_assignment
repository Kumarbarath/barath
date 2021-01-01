import threading
from threading import *
import time
d = {}
#create function
def create(key, value, timeout=0):
    if key in d:
        print("error: this key already exists")  
    else:
        if (key.isalpha()):
            if len(d) < (1024 * 1024 * 1024) and value <= (16 * 1024 * 1024): 
                if timeout == 0:
                    l = [value, timeout]
                else:
                    l = [value, time.time() + timeout]
                if len(key) <= 32:  
                    d[key] = l
            else:
                print("Error: Memory limit exceeded ")  
        else:
            print("Error: Invalind key ,key_name must contain only alphabets and no special characters or numbers")  
#read function
def read(key):
    if key not in d:
        print("Error: Given key  is not in the database. Please enter a valid key") 
    else:
        b = d[key]
        if b[1] != 0:
            if time.time() < b[1]: 
                stri = str(key) + ":" + str(b[0])
                return stri
            else:
                print("error: time-to-live of", key, "has expired")
        else:
            stri = str(key) + ":" + str(b[0])
            return stri
#delete function
def delete(key):
    if key not in d:
        print("Error: Given key is not  in the database. Please enter a valid key")  
    else:
        b = d[key]
        if b[1] != 0:
            if time.time() < b[1]:  
                del d[key]
                print("key is successfully deleted")
            else:
                print("error: time-to-live of", key, "has expired")  
        else:
            del d[key]
            print("key is successfully deleted")
#Function to modify the existing values
def modify(key, value):
    b = d[key]
    if b[1] != 0:
        if time.time() < b[1]:
            if key not in d:
                print("Error: Given key is not in database. Please enter a valid key")  
            else:
                l = []
                l.append(value)
                l.append(b[1])
                d[key] = l
        else:
            print("Error: time-to-live of", key, "has expired") 
    else:
        if key not in d:
            print("Error: Given key is not  in database. Please enter a valid key")  
        else:
            l = []
            l.append(value)
            l.append(b[1])
            d[key] = l
#An infinite loop to call the functions recursively
while(1):
    x=int(input("Enter:\n1.create\n2.read\n3.delete\n4.modify\n"))
    if(x==1):
        input_key=input("Enter the input key as string:")
        input_value=int(input("Enter the value for the key in integer:"))
        input_time=int(input("Enter 1 for the time limit:"))
        print("The given key is sucessfully inserted")
        if(input_time==1):
            create(input_key,input_value,input_time)
        else:
            create(input_key,input_value)
    elif(x==2):
            input_key=input("Enter the key to find:")
            read_result=read(input_key)
            print(read_result)
    
    elif(x==3):
            input_key=input("Enter the key  to delete:")
            delete(input_key)
    elif(x==4):
          input_key=input("Enter the  key which you want to modify:")
          input_value=int(input("Enter the value for the key:"))
          modify(input_key,input_value)
    else:
        print("Exit")
        break              
            
