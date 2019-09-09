# Cytes-Ticket
## 求中奖彩票的张数——中兴笔试题（2019.09.09）

## code

    def func(d,tf,tb):
        if len(tb)==0 or len(d)==0:
            return False
        if ''.join(tf+tb) in d:
            return True
        flag=False
        if tb[0]==d[0]:
            flag=func(d,tf+[tb[1]],tb[1:])
        elif (tb[0]=='o' or tb[0]=='a') and (d[0]=='o' or d[0]=='a'):
            flag=func(d,tf+[tb[1]],tb[1:])
        elif (tb[0]=='t' or tb[0]=='l') and (d[0]=='t' or d[0]=='l'):
            flag=func(d,tf+[tb[1]],tb[1:])
        if flag:
            return True
        return flag or func(d,tf,tb[1:])
    ac=0
    for item in tickets:
        if func(drawString,[],list(item)):
            ac+=1
    print(ac)

## 测试用例：
    #输入：
    #numTickets #=3 彩票张数
    #drawString #="aabacd" #抽奖字符串s
    #tickets #={"abocde","aoc","actld"} #彩票列表
    
    #输出：
    #2
