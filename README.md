# HW_4_1

#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Wed Feb 28 14:15:03 2024

@author: fredpvellla
"""

'''
CSC-103 - Homework 4_1 Professor Auerbeck, Fred P Vella
In this assignment, we will build off of out work from the last 
Project. We will:
    1. Add validated members into the Pokemon data set. 
    2. If they do exist in the dataset add them to the dictionary
    3. Under manage team option, they are given the nickname 
option. 
    4. They are given the opportunity to delete their nickname
    in the manage team option. 
    5. Users will still be able to generate a random team 
    with the requirements of an id and dictionary entry. 
    6. Ensure users can delete a pokemon from the list by name. 
'''

import pandas as pd

p=pd.read_csv("data/pokemon.csv")

team=[]

# First, we import necessary data sets. 
# Then, we have an empty data set to be later filled by 
# The pokemon user interaction below. 

# Concurrently, we add four vairables such as 
# 1. Add teammate
# 2. Add nickname
# 3. Exit
# 4. Manage Team

# These beginning variables take the user to their repsective 
# Locations. 

while True:
   
    
    n=input("What would you like to do:\n\n\t1) Add teammate\n\t2) Add nickname\n\t3) Exit\n\t4) Manage Team\n\ninput: ")
    if int(n)==1:
        z=input("What would you like to do:\n\n\t1) Add Teammate\n\t2) Add nickname\n\t3) Exit\n\t4) Generate random team\n\ninput: ")
        if int(z)==1:
            t=input("Who is your teamate: ")
            if len(team) == 3:
                print("Too many teammates")
            if len(team) == 2:
                print("Add a nickname")
                continue
            elif p.loc[p['identifier']==t].empty:
                print("Invalid Pokemon")
                continue
            team.append(t)
            print(team)
        if int(z)==2:
            team = p.sample(n=6)['identifier'].tolist()
            print(team)
    if int(n)==1:
        c=input("What would you like to do:\n\n\t1) Change Order\n\t2) Add Nickname\n\n\t3) Delete Pokemon\ninput:")
        if int(c)==1:
            move=input("Who would you like to move:")
            if move in team:
                to=input("Where would you like to move them to: ")
                i=team.index(move)
                if i == int(to):
                    print("They're already there!")
                if i == int(c) == 3:
                    print("Add Nickname")
                else:
                    team.pop(i)
                    team.insert(int(to),move)
                    print(team)
        if int(c)==3:
            drop=input("Who would you like to remove: ")
            if drop in team:
                i=team.index(drop)
                team.pop(i)
                print(team)
    if int(n)==3:
        print("Exiting...")
        print(team)
        break    

# The function to add a nickname is in the first set of 
# Questions given to the user. All functions, 1,2,3,4 are 
# Supposed to let the user go to their respective functions. 
# There are also functions to delete a pokemon, and to 
# Generate random teams. As well as, delete and change
# Pokemon nicknames. There are also id and dictionary features
# These can also be changed at the user's discretion. 
# The user can also delete a pokemon from the list by name. 
