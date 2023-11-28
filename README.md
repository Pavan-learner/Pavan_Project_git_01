# In this project we are going create a time-table generator.
import random

# This method will randomly select "n" items from a list and returns a unique list.
def generator(list,no_cls):
    l2 = []

    while len(l2) != no_cls:
        res = random.choice(list)
        if res in l2:
            continue
        else:
            l2.append(res)

    return l2

def create_time_table(l,no_day,no_cls):
    days = ["Monday","Tuesday ","Wednesday"," Thursday","Friday","Saturday"]

    with open("time_table.txt", "w") as f:
        f.write(f'''TIME-TABLE FOR {no_day} day's
                           ''')

    for i in range(no_day):
        with open("time_table.txt", "a") as f:
            f.write(f'''
{days[i]}  = {generator(l, no_cls)} 
                       ''')


# Main function

no_subjects = int(input("How many subjects you have: "))
subjects = []

print("NOTICE: !!!!!! The subjects name should be unique !!!!!")
for x in range(no_subjects):
    res = input(f"Enter the subject {x+1} name  : ")
    if(res in subjects):
        print("The subjects should be unique")
        break

    else:
        subjects.append(res)

no_cls = int(input("How many classes per day: "))

if no_cls > no_subjects:
    print("Your no_cls greater than total subjects !!!!!")

else:
    days = int(input("For how many days you want to create a time table: "))

    print("\n")
    create_time_table(subjects,days,no_cls)
    print('The Time table is created!!!!')
