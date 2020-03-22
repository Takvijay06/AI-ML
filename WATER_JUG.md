# 2 WATER JUG PROBLEM  
# WATER JUG PROBLEM

#create a class
class graph:
    n=0
    a=int()
    b=int()
    p=int()

case=[[0,0]]
mt=[(0,0)]
obj={}
main=mt
obj[graph.n]=graph()
obj[graph.n].a=0
obj[graph.n].b=0
obj[graph.n].p=-1

#function on operation on jug
def fillA(case,parent=int()):
    l=len(case)
    for j in range(1,l+1):
        c=0
        clist=[[3,case[j-1][1]]]
        for i in case:
            if i == clist[0]:
                c=c+1
        if(c==0):
            case.append(clist[0])
            mt.append((clist[0][0],clist[0][1]))
            graph.n=graph.n+1
            obj[graph.n]=graph()
            obj[graph.n].a=clist[0][0]
            obj[graph.n].b=clist[0][1]
            parent=j-1
            obj[graph.n].p=parent
            #print(parent)
        
def fillB(case,parent=int()):
    l=len(case)
    for j in range(1,l+1):
        c=0
        clist=[[case[j-1][0],4]]
        for i in case:
            if i == clist[0]:
                c=c+1
        if(c==0):
            case.append(clist[0])
            mt.append((clist[0][0],clist[0][1]))
            graph.n=graph.n+1
            obj[graph.n]=graph()
            obj[graph.n].a=clist[0][0]
            obj[graph.n].b=clist[0][1]
            parent=j-1
            obj[graph.n].p=parent
            #print(parent)

def emptyA(case,parent=int()):
    l=len(case)
    for j in range(1,l+1):
        c=0
        clist=[[0,case[j-1][1]]]
        for i in case:
            if i == clist[0]:
                c=c+1
        if(c==0):
            case.append(clist[0])
            mt.append((clist[0][0],clist[0][1]))
            graph.n=graph.n+1
            obj[graph.n]=graph()
            obj[graph.n].a=clist[0][0]
            obj[graph.n].b=clist[0][1]
            parent=j-1
            obj[graph.n].p=parent
            #print(parent)
            
def emptyB(case,parent=int()):
    l=len(case)
    for j in range(1,l+1):
        c=0
        clist=[[case[j-1][0],0]]
        for i in case:
            if i == clist[0]:
                c=c+1
        if(c==0):
            case.append(clist[0])
            mt.append((clist[0][0],clist[0][1]))
            graph.n=graph.n+1
            obj[graph.n]=graph()
            obj[graph.n].a=clist[0][0]
            obj[graph.n].b=clist[0][1]
            parent=j-1
            obj[graph.n].p=parent
            #print(parent)
            
def fillA2B(case,parent=int()):
    l=len(case)
    for j in range(1,l+1):
        c=0
        if(case[j-1][1] < 4 and case[j-1][0] > 0):
            if(case[j-1][0]+case[j-1][1] >= 4):
                clist=[[case[j-1][0]-(4-case[j-1][1]),4]]
            else:
                clist=[[case[j-1][1],case[j-1][0]]]
            for i in case:
                if i == clist[0]:
                    c=c+1
            if(c==0):
                case.append(clist[0])
                mt.append((clist[0][0],clist[0][1]))
                graph.n=graph.n+1
                obj[graph.n]=graph()
                obj[graph.n].a=clist[0][0]
                obj[graph.n].b=clist[0][1]
                parent=j-1
                obj[graph.n].p=parent
                #print(parent)
                

def fillB2A(case,parent=int()):
    l=len(case)
    for j in range(1,l+1):
        c=0
        if(case[j-1][0] < 3 and case[j-1][1] > 0):
            if(case[j-1][0]+case[j-1][1] >= 3):
                clist=[[3,case[j-1][1]-(3-case[j-1][0])]]
            else:
                clist=[[case[j-1][1],case[j-1][0]]]
            for i in case:
                if i == clist[0]:
                    c=c+1
            if(c==0):
                case.append(clist[0])
                mt.append((clist[0][0],clist[0][1]))
                graph.n=graph.n+1
                obj[graph.n]=graph()
                obj[graph.n].a=clist[0][0]
                obj[graph.n].b=clist[0][1]
                parent=j-1
                obj[graph.n].p=parent
                #print(parent)

#possible case and graph
for i in range(0,3):
    fillA(case,graph.n)
    fillB(case,graph.n)
    emptyA(case,graph.n)
    emptyB(case,graph.n)
    fillA2B(case,graph.n)
    fillB2A(case,graph.n)
obj #dictionary having all the case

#finding the path for goal state
for i in obj:
    if obj[i].a==0 and obj[i].b==2:
        temp=i
graph.n=temp
print("Showest path between(down to up): ")
while obj[graph.n].p!=-1:
    print(obj[graph.n].a,obj[graph.n].b)
    graph.n=obj[graph.n].p
print(obj[graph.n].a,obj[graph.n].b)

