import random 
import time
import sys
import datetime

 

def display_log():
        import os
        if os.path.exists("logfile.txt")== False :
            f = open("logfile.txt","wt")
            f.close()
        file = open("logfile.txt",'rt')
        for i in file:
            print(i)
        file.close()    

def search(str1):
    try:
        import os
        if os.path.exists("phonebook.txt")== False :
            f = open("phonebook.txt","wt")
            f.close()
        index = 0
        str1 = str1.lower()  
        f = open("phonebook.txt","rt")
        a = f.read()
        a = a.lower()
        l1 = a.split(' ')
        index = l1.index(str1)       
    except ValueError:
        print(str1,' *****is not in list*****\n')
        
    if index:
        print((">>>>>>> ............... ................... < "+str1.capitalize()+" phone number is >:",l1[index+1]))
        call(str1)
     
        
def call(str1):

    t0 = time.time()
    time.sleep(random.randint(3,5))
    t1 = int(time.time())-int(t0)
    print('\n',t1,' second is lated for calling',str1)
    file_log = "logfile.txt"
    fileObject = open(file_log,'at')
    fileObject.write('***you are calling time is with:' + str1 + ' for ' + str(t1) + ' secend ' + 'in ' + str(datetime.datetime.now()) + '****\n'  )
    fileObject.close()
 
    
def data_entry():
    
    k1=input("Enter name: ")
    v1=input("Eneter number: ")
    f=open("phonebook.txt","at")
    f.write(' '+str(k1)+' '+str(v1)+' \n')
    f.close()


        
def main():
    while True:
        from os import system, name
        time.sleep(5)
        if name == 'nt': 
            _ = system('cls')
        else:
            _ = system('clear')
            
        print('> To Call Type the name:')
        print('>>To ADD type add:  ')
        print('>>> To diplay log type log: ')
        print('>>>>to exit press E key:'+'\n'*4)
        
        l=input("Type one of the above options : ")
        
        if l == 'E' or l == 'e' :
            break
        if l == "add" :
            data_entry()
        elif l == "log":
            display_log()
        else:        
            search(l)
       # input('Press Enter key')   
if __name__ == "__main__":main()





