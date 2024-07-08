import random

# Çöp Adamın başlangıç durumu
health = 10
money = 100
items = []

# İtem listesi
item_list = ["Telefon", "Anahtarlık", "Para", "Yüzük"]

def main():
    global health, money, items
    
    print("Çöp Adam Oyununa Hoş Geldiniz!")
    print("Oyunun amacı sağlık ve para toplamak, ama dikkatli olun, tehlikeli durumlarla karşılaşabilirsiniz!")
    print("=============================================")
    
    while health > 0:
        print("\nSağlık: {}, Para: {}".format(health, money))
        print("İtemler: ", items)
        
        choice = input("\nNe yapmak istersiniz? (a: ara, d: dinlen, ç: çıkış): ").lower()
        
        if choice == 'a':
            search()
        elif choice == 'd':
            rest()
        elif choice == 'ç':
            break
        else:
            print("Geçersiz seçenek, lütfen tekrar deneyin.")
    
    print("\nOyun bitti. Sağlık seviyeniz sıfırlandı.")
    print("Topladığınız para: {}. Topladığınız itemler: {}".format(money, items))

def search():
    global health, money, items
    
    danger = random.randint(1, 10)
    
    if danger <= 5:
        print("\nGüvenli bir yer buldunuz!")
        earn_money = random.randint(10, 50)
        earn_health = random.randint(1, 5)
        
        print("Bulduğunuz para: {} TL".format(earn_money))
        money += earn_money
        print("Bulduğunuz sağlık: {}".format(earn_health))
        health += earn_health
    else:
        print("\nTehlikeli bir bölgeye düştünüz!")
        lose_health = random.randint(1, 10)
        
        print("Kaybettiğiniz sağlık: {}".format(lose_health))
        health -= lose_health

def rest():
    global health
    
    print("\nDinleniyorsunuz...")
    recover_health = random.randint(1, 5)
    print("Toplam {} sağlık kazandınız.".format(recover_health))
    health += recover_health

# Oyunu başlat
if __name__ == "__main__":
    main()
