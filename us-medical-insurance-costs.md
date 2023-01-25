# U.S. Medical Insurance Costs

1)Importing our dataset


```python
import csv
age=[]
sex=[]
bmi=[]
children=[]
smoker=[]
region=[]
charges=[]
with open("insurance.csv",newline='') as insurance_csv:
    reader=csv.DictReader(insurance_csv)
    for row in reader:
        age.append(int(row["age"]))
        sex.append(row["sex"])
        bmi.append(float(row["bmi"]))
        children.append(int(row["children"]))
        smoker.append(row["smoker"])
        region.append(row["region"])
        charges.append(float(row["charges"]))
#Created lists containing the data from our 7 variables, after importing the dataset.
```

2)What is the average age of our sample?


```python
def average(l): #A function that calculates averages for my lists
    total=0
    for i in l:
        total+=i
    return total/len(l)
print("Average age is",format(average(age),'.2f'))
```

    Average age is 39.21
    

3)What are the average charges/children/bmi of our sample?


```python
print("Average charges are",format(average(charges),'.2f'))
print("Average children are",format(average(children),'.2f'))
print("Average bmi is",format(average(bmi),'.2f'))
```

    Average charges are 13270.42
    Average children are 1.09
    Average bmi is 30.66
    

4)Where the majority of people are from?


```python
count_southeast=0
count_southwest=0
count_northwest=0
count_northeast=0
for area in region:
    if area=="southeast":
        count_southeast+=1
    elif area=="southwest":
        count_southwest+=1
    elif area=="northeast":
        count_northeast+=1
    else:
        count_northwest+=1
print("The percentage of southeast region in our dataset is "+str(format(count_southeast/len(region)*100,'.2f'))+"%")
print("The percentage of southwest region in our dataset is "+str(format(count_southwest/len(region)*100,'.2f'))+"%")
print("The percentage of northeast region in our dataset is "+str(format(count_northeast/len(region)*100,'.2f'))+"%")
print("The percentage of northwest region in our dataset is "+str(format(count_northwest/len(region)*100,'.2f'))+"%")
        
```

    The percentage of southeast region in our dataset is 27.20%
    The percentage of southwest region in our dataset is 24.29%
    The percentage of northeast region in our dataset is 24.22%
    The percentage of northwest region in our dataset is 24.29%
    

5)How much is the average charges for smoker vs no-smoker?


```python
total_yes=0
smokers=0
total_no=0
no_smokers=0
for i in range(len(smoker)):
    if smoker[i]=="yes":
        total_yes+=charges[i]
        smokers+=1
    else:
        total_no+=charges[i]
        no_smokers+=1
print("Average charges for a smoker",format(total_yes/smokers,'.2f'))
print("Average charges for a no-smoker",format(total_no/no_smokers,'.2f'))
        
```

    Average charges for a smoker 32050.23
    Average charges for a no-smoker 8434.27
    

6)How much is the average charges for male vs female?


```python
total_male=0
males=0
total_female=0
females=0
for i in range(len(sex)):
    if sex[i]=="male":
        total_male+=charges[i]
        males+=1
    else:
        total_female+=charges[i]
        females+=1
print("Average charges for a male",format(total_male/males,'.2f'))
print("Average charges for a female",format(total_female/females,'.2f'))
```

    Average charges for a male 13956.75
    Average charges for a female 12569.58
    

7)How children affect charges?


```python
def maximum(l):    #created a function that calculates max and max position from my lists with arithmetic data
    maximum=0
    for i in range(len(l)):
        if l[i]>maximum:
            maximum=l[i]
    return maximum
maximum(children)

total_1=0
child1=0
total_2=0
child2=0
total_3=0
child3=0
total_4=0
child4=0
total_5=0
child5=0
for i in range(len(children)):
    if children[i]==1:
        total_1+=charges[i]
        child1+=1
    elif children[i]==2:
        total_2+=charges[i]
        child2+=1
    elif children[i]==3:
        total_3+=charges[i]
        child3+=1
    elif children[i]==4:
        total_4+=charges[i]
        child4+=1
    else:
        total_5+=charges[i]
        child5+=1
print("Average charges for a 1 child",format(total_1/child1,'.2f'))
print("Average charges for a 2 children",format(total_2/child2,'.2f'))
print("Average charges for a 3 children",format(total_3/child3,'.2f'))
print("Average charges for a 4 children",format(total_4/child4,'.2f'))
print("Average charges for a 5 children",format(total_5/child5,'.2f'))
        
        
```

    Average charges for a 1 child 12731.17
    Average charges for a 2 children 15073.56
    Average charges for a 3 children 15355.32
    Average charges for a 4 children 13850.66
    Average charges for a 5 children 12257.13
    

8)How much region affects charges?


```python
total_r1=0
r1=0
total_r2=0
r2=0
total_r3=0
r3=0
total_r4=0
r4=0
for i in range(len(region)):
    if region[i]=="southeast":
        total_r1+=charges[i]
        r1+=1
    elif region[i]=="southwest":
        total_r2+=charges[i]
        r2+=1
    elif region[i]=="northeast":
        total_r3+=charges[i]
        r3+=1
    else:
        total_r4+=charges[i]
        r4+=1

print("Average charges for southeast region",format(total_r1/r1,'.2f'))
print("Average charges for southwest region",format(total_r2/r2,'.2f'))
print("Average charges for northeast region",format(total_r3/r3,'.2f'))
print("Average charges for northwest region",format(total_r4/r4,'.2f'))

```

    Average charges for southeast region 14735.41
    Average charges for southwest region 12346.94
    Average charges for northeast region 13406.38
    Average charges for northwest region 12417.58
    

9)How much bmi affects charges?


```python
total_bmi1=0
bmi1=0
total_bmi2=0
bmi2=0
total_bmi3=0
bmi3=0
total_bmi4=0
bmi4=0
for i in range(len(bmi)):
    if bmi[i]>=30:
        total_bmi1+=charges[i]
        bmi1+=1
    elif bmi[i]>=25:
        total_bmi2+=charges[i]
        bmi2+=1
    elif bmi[i]>=20:
        total_bmi3+=charges[i]
        bmi3+=1
    else:
        total_bmi4+=charges[i]
        bmi4+=1

print("Average charges for bmi>=30",format(total_bmi1/bmi1,'.2f'))
print("Average charges for bmi>=25 and <30",format(total_bmi2/bmi2,'.2f'))
print("Average charges for bmi>=20 and <25",format(total_bmi3/bmi3,'.2f'))
print("Average charges for bmi<20",format(total_bmi4/bmi4,'.2f'))

```

    Average charges for bmi>=30 15552.34
    Average charges for bmi>=25 and <30 10987.51
    Average charges for bmi>=20 and <25 10572.37
    Average charges for bmi<20 8838.56
    

10)How much age affects charges?


```python
total_a1=0
a1=0
total_a2=0
a2=0
total_a3=0
a3=0
total_a4=0
a4=0
for i in range(len(age)):
    if age[i]>=50:
        total_a1+=charges[i]
        a1+=1
    elif age[i]>=35:
        total_a2+=charges[i]
        a2+=1
    elif age[i]>=20:
        total_a3+=charges[i]
        a3+=1
    else:
        total_a4+=charges[i]
        a4+=1

print("Average charges for age>=50",format(total_a1/a1,'.2f'))
print("Average charges for age>=35 and <50",format(total_a2/a2,'.2f'))
print("Average charges for age>=20 and <35",format(total_a3/a3,'.2f'))
print("Average charges for age<20",format(total_a4/a4,'.2f'))
```

    Average charges for age>=50 17902.55
    Average charges for age>=35 and <50 13744.29
    Average charges for age>=20 and <35 10094.28
    Average charges for age<20 8407.35
    

Now, we will create a dictionary to make easy for to do further analysis in the future.


```python
insurance_dict={"age":age,"sex":sex,"bmi":children,"smoker":smoker,"region":region,"charges":charges}
```

After this analysis, we found out that a high bmi and age, in addition with smoking, force us to pay more for a health insurance. In conclusion, if we want to live many years, we must maintain our bmi in regular levels and quit smoking.
