import mysql.connector as a
from random import randint
from time import sleep

conn = a.connect(host='localhost', user='root', password='12345', database='gowtham')
x = conn.cursor(buffered=True)
cho = 0
while True:
    print('************************************************************\n')
    print('1. Login\n2. Signin\n3. Exit\n')
    print('************************************************************\n')
    sleep(1)
    cho = int(input('Enter your choice :'))
    if cho == 2:
        sleep(1)
        found='y'
        while found=='y':
            name = input('Enter your name :').capitalize()
            passw = input('Enter your password :')
            amount = input('Enter your amount :')
            x.execute('select * from player')
            found = 'n'
            for i in x:
                if name == i[0]:
                    print('\nUser name already used\n')
                    found = 'y'
        if found == 'n':
            query = 'insert into player values(%s,%s,%s)'
            val = (name, passw, amount)
            x.execute(query, val)
            conn.commit()
            print()
            print('************************************************************\n')
            sleep(1)
            print('Signin completed successfully')
            print('Login with your name')
    else:
        break

if cho == 1:
    class Player:
        def __init__(self, name, passw, amount):
            self.name = name
            self.passw = passw
            self.amount = amount


    name = input('Enter your name :').capitalize()
    passw = input('Enter your password :')
    x.execute('select * from player')
    found = 'n'
    for i in x:
        p='y'
        if i[0] + i[1] == name + passw:
            player = Player(i[0], i[1], int(i[2]))
            sleep(1)
            print()
            print('************************************************************\n')
            print('Welcome ' + player.name)
            while True:
                sleep(1)
                print('\n1.Play games\n2.View account details\n3.Exit\n')
                sleep(1)
                cho_ = int(input('Enter your choice :'))
                sleep(1)
                if cho_ == 2:
                    print()
                    print('Name    :' + player.name + '\nAmount  :' + str(player.amount) + '\n')
                    print('************************************************************')
                elif cho_ == 1:
                    print('\nEntry fee : $5')
                    sleep(0.5)
                    print('Wining price :$250\n')
                    ans ='n'
                    ans = input('Do you want to play:').lower()
                    while ans == 'y':
                        if player.amount >= 5:
                            player.amount = player.amount - 5
                            num1 = randint(0, 9)
                            num2 = randint(0, 9)
                            num3 = randint(0, 9)
                            #num1=1
                            #num2=1
                            #num3=1
                            print()
                            print(num1,end=' | ')
                            sleep(1)
                            print(num2, end=' | ')
                            sleep(1)
                            print(num3)
                            if num1 == num2 == num3 :
                                sleep(1)
                                print('\nYOUUUUU  WONNNNN')
                                player.amount = player.amount + 250
                            else:
                                print('\nYOU LOST ')
                            ans = input('\nDo you want to play again:').lower()
                        else :
                            print('Low amount')
                            break
                elif cho_ == 3:
                    quer="update player set amount = %s where name = %s"
                    val=(str(player.amount),player.name)
                    x.execute(quer,val)
                    conn.commit()
                    print('Thank You')
                    break
                elif cho_ != 1 and cho_ != 2 and cho_ != 3:
                    print('Wrong input')

        elif i[0] + i[1] != name + passw:
            p='n'
    if p=='n':
        print('Name or Password wrong')
