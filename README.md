
import mysql.connector as p 
dat=p.connect(host="localhost",user="root",passwd="purva",database="school") 
#for student 
#to add new student
def addnewStudent():
     k=int(input("how many records of  student you want to add??????"))
    for i in range(k):
             grno=int(input("Enter Grno :")) 
             sname=input("Enter Name:") 
             rno=int(input("Enter Rollno:")) 
             pho=int(input("Enter Phone Number:")) 
             add=input("Enter Address:") 
             sclass=int(input("Enter Class:")) 
             shouse=input("Enter House:") 
             c1=dat.cursor() 
             query="insert into Student (Grno,StuName,Rollno,Phone,Address,SClass,SHouse)values('{}','{}','{}','{}','{}','{}','{}')".format(grno,sname,rno,pho,add,sclass,shouse) 
             c1.execute(query) 
             dat.commit() 
             print("Record Added Successfully") 
             h=input("do you want to enter    more records???(y/n)")
             if h=='n':
                break
             c1.close()            
   




             
#to display student record
def displayStudent(): 
 c1=dat.cursor() 
 c1.execute("select * from Student") 
 data=c1.fetchall() 
 print("-------------------------------------------------------------------------------------------------------") 
 print("Grno\tSName\t\tRno\t\tPhone\t\t\tAddress\t\tCls\t\tHouse") 
 print("--------------------------------------------------------------------------------------------------------") 
 for row in data: 
    print(row[0],"\t\t",row[1],"\t\t",row[2],"\t\t",row[3],"\t\t",row[4],"\t\t",row[5],"\t\t",row[6]) 
 print("------------------------------------------------------------------------------------------------------") 
 c1.close()
 
     
         
     
     
         
       
     




       #to update the student record 
     
          def updateStudent(): 
 c1=dat.cursor() 
 if dat: 
      Grno=input("Enter Grno.: ") 
      query="select * from Student where Grno='{}'".format(Grno) 
      c1.execute(query) 
      data=c1.fetchall() 
 if data: 
    print ("*ENTER $ FOR UPDATING ROLLNO*") 
    print ("*ENTER # FOR UPDATING PHONE*") 
    print ("*ENTER @ FOR UPDATING ADDRESS*") 
    print ("*ENTER ^ FOR UPDATING HOUSE*")
    print ("*ENTER & FOR UPDATING CLASS*") 
    symbol=input("Please Enter Your Choice : ")
    
   if symbol=='$': 
           rollno=input("Enter rollno of the student:") 
           query="update  Student set Rollno='{}' where Grno='{}'".format(rollno,Grno) 
           c1.execute(query) 
           dat.commit() 
           print("Record Updated")

    elif symbol=='#': 
           phone=input("Enter phone no :") 
           query="update Student set Phone='{}' where Grno='{}'".format(phone,Grno)
 
           c1.execute(query) 
           dat.commit() 
           print("Record Updated") 
    elif symbol=='@': 
           address=input("Enter address of the student:") 
           query="update Student set Address='{}' where Grno='{}'".format(address,Grno) 

           c1.execute(query) 
           dat.commit() 
           print("Record Updated") 
    elif symbol=='^': 
           house=input("Enter house of the student:") 
           query="update Student set SHouse='{}' where Grno='{}'".format(house,Grno)
 
           c1.execute(query) 
           dat.commit() 
           print("Record Updated")
    
    elif symbol=='&': 
          clas=int(input("Enter class of the student:")) 
          query="update Student SET SClass='{}' where Grno='{}'".format(clas,Grno)
 
          c1.execute(query) 
          dat.commit() 
          print("Record Updated") 
    else: 
     print("Please enter Correct symbol !!!") 
 else: 
    print("Wrong Grno Is Entered…Try Again !!!")
 
#to delete the student record
 
def deleteStudent(): 
     grno=input("Enter Grno of the student:") 
     c1=dat.cursor() 
     query="delete from Student where Grno='{}'".format(grno) 
c1.execute(query) 
     dat.commit() 
     print("Record is Deleted sucessfully......") 
     c1.close() 
             dat.close()
      #for teacher
#to add new teacher record
 
def addnewTeacher():
    j=int(input("how many records of teacher you want to add?????"))
    for i in range(j):
             tid=int(input("Enter teacher id :")) 
             tname=input("Enter Name:") 
             tpho=int(input("Enter Phone Number:")) 
             tadd=input("Enter Address:") 
             c1=dat.cursor() 
             query="insert into Teacher(Teid,TeName,TePhone,TeAddress) values ('{}','{}','{}','{}')".format(tid,tname,tpho,tadd) 
             c1.execute(query)
             dat.commit() 
             print("Record Added.....") 
             f=input("do you want to enter more records???(y/n)")
             if f=='n':
                break
             c1.close()
 
# to display teacher record
def displayTeacher(): 
        c1=dat.cursor() 
        c1.execute("select * from Teacher") 
        data=c1.fetchall() 
        print("----------------------------------------------------------------------")
        print("Teacherid\tTeacherName\t\tPhone\t\tAddress ") 
        print("-----------------------------------------------------------------------")
    
        for row in data: 
              print(row[0],"\t","\t",row[1],"\t",row[2],"\t",row[3]) 
        print("------------------------------------------------------------------------")
        c1.close()
 
#to update teacher record
def updateTeacher(): 
 c1=dat.cursor() 
 if dat: 
    tid=input("Enter Teacher id: ") 
    query="select * from Teacher where Teid='{}'".format(tid) 
    c1.execute(query) 
    data=c1.fetchall() 
 if data:
     print ("ENTER * FOR TEACHER NAME") 
     print ("ENTER @ FOR TEACHER PHONE") 
     print ("ENTER % FOR TEACHER ADDRESS") 
 
     sym=input("Please Enter Your Choice : ")
     if sym=='*': 
              name=input("Enter name of the teacher:") 
              query="update Teacher set TeName='{}' where Teid='{}'".format(name,tid) 
              c1.execute(query) 
              dat.commit() 
              print("Record Updated......") 
     elif sym=='@': 
              phone=input("Enter phone no :") 
              query="update Teacher set TePhone='{}' WHERE Teid='{}'".format(phone,tid) 
              c1.execute(query) 
              dat.commit() 
              print("Record Updated sucessfully......") 
     elif sym=='%': 
               address=input("Enter address of the teacher:") 
               query="update Teacher set TeAddress='{}' where Teid='{}'".format(address,tid) 
               c1.execute(query) 
               dat.commit()
               print("Record Updated sucessfully.....") 
     else: 
         print("Please Enter Correct symbol !!!") 
 else: 
    print("incorrect id Is Entered !!!")

#to delete teacher record
def deleteTeacher(): 
     tid=input("Enter Teacher id :") 
     c1=dat.cursor() 
     query="delete from Teacher where Teid='{}'".format(tid) 
     c1.execute(query) 
     dat.commit() 
     print("Record Deleted") 
     c1.close()
     dat.close()

#MAIN

print("\n...........SCHOOL MANAGEMENT SYSTEM .......") 
print("\n ...............MADE BY : PURVANGI PATEL...\n") 

for i in range(1): 
     print("---------------------------------------------") 
     print(" what task you want to perform????? \n") 
     print(" ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^") 
     print(" Enter 1 :: Add New Student ") 
     print(" Enter 2 :: Display Student Data ") 
     print(" Enter 3 ::Update Student Data ") 
     print(" Enter 4 :: Add New Teacher record ") 
     print(" Enter 5 :: Display Teacher Data ") 
     print(" Enter 6 :: Update Teacher Data ") 
     print(" Enter 7 :: Delete a Student Record ") 
     print(" Enter 8 :: Delete a Teacher Record ") 
     print(" Enter 9 :: way out!!!!") 
     print(" ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^") 
     print("---------------------------------------------") 
    yr_choice=int(input(" Please Enter Your Choice from above : "))
if yr_choice==1:
         print("please enter the following  details : ")
         addnewStudent() 
     elif yr_choice==2:
         print("please enter the following  details : ")
         displayStudent() 
     elif yr_choice==3:
         print("please enter the following  details : ")
         updateStudent() 
     elif yr_choice==4: 
         print("please enter the following  details : ")
         addnewTeacher() 
     elif yr_choice==5:
         print("please enter the following  details : ")
         displayTeacher() 
     elif yr_choice==6:
         print("please enter the following  details : ")
         updateTeacher() 
     elif yr_choice==7:
         print("please enter the following  details : ")
         deleteStudent() 
     elif yr_choice==8:
         print("please enter the following  details : ")
         deleteTeacher() 
     elif yr_choice==9: 
       print("Thank you ....for using school mangement system...") 
     break 
else: 
       print(".....your choice does not exist ....sorry ") 
              
dat.close()








 




  
