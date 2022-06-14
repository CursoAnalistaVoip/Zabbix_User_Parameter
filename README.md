
# Zabbix_User_Parameter
Como utilizar o **UserParameter** para monitorar o Asterisk.
> Às vezes você pode querer executar uma verificação  que não vem pré definido no Zabbix
> Com o UserParameter é possivél realizar esse tipo de verificação.



A sintaxe do **UserParameter** é  :eyes:


> **UserParameter=< chave_do_item >,< comando >**
>  
> 
  Exemplo:
  
  UserParameter=linha.voip,sudo /usr/sbin/asterisk -rx "pjsip show registrations" | grep 5857658 | grep Registered | wc -l
  
  ![Captura de tela de 2022-06-13 23-49-20](https://user-images.githubusercontent.com/102430464/173483024-f7f47b01-a261-47b1-b69f-616ff9dfe8aa.png)
  
  ![Captura de tela de 2022-06-13 23-50-15](https://user-images.githubusercontent.com/102430464/173483121-55c7ca12-8166-4bd4-a9e2-b92fc71f730d.png)
  
  ![Captura de tela de 2022-06-13 23-51-49](https://user-images.githubusercontent.com/102430464/173483327-bc015137-8a9d-4622-8caa-cba616514876.png)


  Esse comando nos trouxe o resultado **0** , poís a conta SIP 5857658 não está registrada.
  
  
  


Agora se faz necessario dar permissão no sudoers do Linux:


vim /etc/sudoers.d/user_zabbix


> #Allow the user zabbix to execute any command without password
> 
> Defaults:zabbix !requiretty
> 
> zabbix  ALL=(ALL:ALL) NOPASSWD:/usr/sbin/asterisk

![Captura de tela de 2022-06-13 23-44-53](https://user-images.githubusercontent.com/102430464/173482560-9487a7e3-2bf0-43df-8125-86d5f5570396.png)

 #Reinicie o serviço do Zabbix Agent: :+1: 
> **systemctl restart zabbix-agent**


Agora vamos criar nosso Template  no Zabbix e adicionar esse Item   :clap:


![Captura de tela de 2022-06-14 00-01-35](https://user-images.githubusercontent.com/102430464/173484639-6a3cbfa2-2f9c-4741-a8a5-73d93dccd5a5.png)

![Captura de tela de 2022-06-14 00-02-13](https://user-images.githubusercontent.com/102430464/173484660-1966cdff-ec62-4773-9d1d-4bfd28aeeb74.png)

![Captura de tela de 2022-06-14 00-05-13](https://user-images.githubusercontent.com/102430464/173484888-52432fa5-9053-421e-935f-c78e1de9d358.png)


![Captura de tela de 2022-06-14 00-07-25](https://user-images.githubusercontent.com/102430464/173485202-758961e3-693f-408b-bfb0-64375555708d.png)

![Captura de tela de 2022-06-14 00-08-44](https://user-images.githubusercontent.com/102430464/173485318-e2a1fc9f-26ef-4586-8174-46bfca65648d.png)

![Captura de tela de 2022-06-14 00-14-57](https://user-images.githubusercontent.com/102430464/173485931-24005c53-9177-45fa-aace-2fd7f7c0b9c3.png)







