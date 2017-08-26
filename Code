import pymongo
import json
from pymongo import MongoClient
client = MongoClient()
db = client.client_database1
collection = db.client_collection
while True:
    
    print("\n1. Exit")
    print("2. Insert Data")
    print("3. View Data")
    print("4. Update Data")
    print("5. Delete Data")
    choice = int(input("Enter Choice: "))
    if choice==1:
        break
  
    elif choice==2:
        print("\n")
        fn_ip = input("Enter First Name: ")
        sur_ip = input("Enter Surname: ")
        cell_ip = input("Enter Cell: ")
        city_ip = input("Enter City: ")
        pro_ip = input("Enter Profession: ")
        model_ip = input("Enter Car Model: ")
        year_ip = input("Enter Car Manufacturing Year: ")
        value_ip = input("Enter Car Value: ")
    
        post = {
            'first_name': fn_ip,
            'surname': sur_ip,
            'cell': cell_ip,
            'city': city_ip,
            'profession': pro_ip,
            'cars':
                {
                    'model': model_ip,
                    'year': year_ip,
                    'value': value_ip
                }
        }
        collection.insert_one(post)
        print("Record Inserted Successfully!\n")
    elif choice==3:
        print("\n1. View All")
        print("2. View as per mentioned key:value")
        ch = int(input("Enter Choice: "))
        if ch==1:
            posts = collection.find()
            que = {} 
            #cars = {}
            for post in posts:
                #print(post)
                que=post
                print(que['first_name'],que['surname'],que['cell'],que['city'],que['profession'],que['cars'])
            #query = collection.find({"cars.value": {"$in": ["500000","400000"]}})
            #print("For Car Model:Suzuki and Surname:Miller")
            #query = collection.find({"cars.model":"Suzuki","surname":"Bale"})
            #query = collection.find({"$or":[{"first_name":"Kenny"},{"first_name":"Tom"}]})
            #query = collection.find({"cars.value": {"$in": ["500000","400000"]}},{"first_name":1,"cell":1})
            '''
            for q in query:
                #print(post)
                que=q
                print(que['first_name'],que['surname'],que['cell'],que['city'],que['profession'],que['cars'])
            '''
        elif ch==2:
            field_name = input("\nEnter Field Name: ")
            value = input("Enter Field Value: ")
            if (field_name=="model") or (field_name=="year") or (field_name=="value"):
                f_name="cars."+field_name
                query = collection.find({f_name:value})
            else:
                query = collection.find({field_name:value})
            que = {}
            for q in query:
                #print(q)
                que=q
                print("\nData")
                print(que['first_name'],que['surname'],que['cell'],que['city'],que['profession'],que['cars'])
    elif choice==4:
        field_name = input("\nEnter Field Name: ")
        value = input("Enter Field Value: ")
        field_name1 = input("Enter Field Name whose value is to be updated: ")
        value1 = input("Enter New Field Value: ")
        
        #if field_name!="":
        if (field_name=="model") or (field_name=="year") or (field_name=="value"):
            f_name="cars."+field_name
            if (field_name1=="model") or (field_name1=="year") or (field_name1=="value"):
            #if field_name1!="":
                f_name1="cars."+field_name1
                #query = collection.find({f_name:value})
                query = collection.update_many({f_name:value},{"$set":{f_name1:value1}})
                print(query.matched_count,"record matched")
                print(query.modified_count,"record modified")
            else:
                query = collection.update_many({f_name:value},{"$set":{field_name1:value1}})
                print(query.matched_count,"record matched")
                print(query.modified_count,"record modified")
        elif (field_name=="first_name") or (field_name=="surname") or (field_name=="cell") or (field_name=="city") or (field_name=="profession"):
            if (field_name1=="model") or (field_name1=="year") or (field_name1=="value"):
                f_name1="cars."+field_name1
                #query = collection.find({f_name:value})
                query = collection.update_many({field_name:value},{"$set":{f_name1:value1}})
                print(query.matched_count,"record matched")
                print(query.modified_count,"record modified")
            else:
                query = collection.update_many({field_name:value},{"$set":{field_name1:value1}})
                print(query.matched_count,"record matched")
                print(query.modified_count,"record modified")
            #query = collection.find({field_name:value})
    elif choice==5:
        print("\n1. Delete All")
        print("2. Delete as per mentioned key:value")
        ch = int(input("Enter Choice: "))
        if ch==2:
            field_name = input("\nEnter Field Name: ")
            value = input("Enter Field Value: ")
            if (field_name=="model") or (field_name=="year") or (field_name=="value"):
                f_na3me="cars."+field_name
                result = collection.delete_many({f_name:value})
                print(result.deleted_count,"record deleted")
            else:
                result = collection.delete_many({field_name:value})
                print(result.deleted_count,"record deleted")
        elif ch==1:
            result = collection.delete_many({})
            print(result.deleted_count,"record deleted")
        
