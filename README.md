# TG_Scrap

Данный скрипт парсит участников групп тг. Для того, чтобы спарсить участников чата, вам необходимо самому быть участником данного чата.

# Инструкция к запуску скрипта

Для начала вам необходимо зарегестрироваться на сайте https://my.telegram.org/auth, создать приложение и получить api_id и api_hash.

Далее мы вставляем данные в скрипт, в указанныз местах.

После чего установить пару модулей:

    pip install csv
      
    pip install telethon

ВСЁ! Осталось только запустить, вставить полученный код и выбрать чат для скрапинга.

# Добавление проспама по людям (код кривой, но пойдёт, потому что написан за 3 минуты)

Просто нужно вставить этот кусок кода в конце

        count = 0

        cl2 = 1
        cl3 = 0
        cl4 = 0
        
        message = '' #Текст сообщения для проспама

        with open('members.csv') as f:
            reader = csv.reader(f)
            for row in reader:
                if count < 5:
                    if row[0] == "":
                        pass
                        print('""')
                    else:
                        if cl2 == 1:
                            client2.send_file(row[0], 'photo.png', caption=message) #Вместо photo.png вставь название своей картинки
                            print(row[0])

                            cl2 = 0
                            cl3 = 1
                            cl4 = 0

                        elif cl3 == 1:
                            client2.send_file(row[0], 'photo.png', caption=message) #Вместо photo.png вставь название своей картинки
                            print(row[0])

                            cl2 = 0
                            cl3 = 0
                            cl4 = 1

                        elif cl4 == 1:
                            cl2 = 1
                            cl3 = 0
                            cl4 = 0

                    time.sleep(2)
                    count += 1

                elif count == 5:
                    count = 0
                    time.sleep(10)
                    
 
