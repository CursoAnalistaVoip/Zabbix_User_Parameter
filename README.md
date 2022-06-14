# Zabbix_User_Parameter
Como utilizar o **UserParameter** para monitorar o Asterisk.
> Às vezes você pode querer executar uma verificação  que não vem predefinido com Zabbix.
> Com o UserParameter é possivél realizar esse tipo de verificação.



A sintaxe do UserParameter é  :eyes:


> **UserParameter=< chave_do_item >,< comando >**
>  
> 
  Exemplo:
  
  
# systemctl status nginx

 
![Captura de tela de 2022-06-13 23-27-37](https://user-images.githubusercontent.com/102430464/173480871-ea07ea6f-3c80-42ad-b328-4a09988008de.png)

# systemctl status nginx | grep running > /dev/null 2>&1 ; echo $?

![Captura de tela de 2022-06-13 23-32-25](https://user-images.githubusercontent.com/102430464/173481108-a06b47ca-5801-4627-9f7a-57ab4a27b12e.png)

# UserParameter=status.nginx, systemctl status nginx | grep running > /dev/null 2>&1 ; echo $?

![Captura de tela de 2022-06-13 23-33-48](https://user-images.githubusercontent.com/102430464/173481326-6b62c222-3233-4826-9019-861aadfbe554.png)
