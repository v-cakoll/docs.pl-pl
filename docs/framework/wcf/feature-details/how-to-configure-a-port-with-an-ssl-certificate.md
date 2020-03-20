---
title: 'Instrukcje: Konfigurowanie portu z certyfikatem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185109"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Instrukcje: Konfigurowanie portu z certyfikatem SSL

Podczas tworzenia samodzielnej usługi Windows Communication Foundation (WCF) z klasą, <xref:System.ServiceModel.WSHttpBinding> która używa zabezpieczeń transportu, należy również skonfigurować port z certyfikatem X.509. Jeśli usługa jest niesymamożna hostowania, można hostować usługę w internetowych usługach informacyjnych (IIS). Aby uzyskać więcej informacji, zobacz [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego, który jest uruchomiony na komputerze.  
  
 Jeśli używasz systemu Windows Server 2003, użyj narzędzia HttpCfg.exe. W systemie Windows Server 2003 to narzędzie jest zainstalowane. Aby uzyskać więcej informacji, zobacz [Przegląd httpcfg](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)). Dokumentacja [narzędzi pomocy technicznej systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) wyjaśnia składnię narzędzia Httpcfg.exe.  
  
 Jeśli korzystasz z systemu Windows Vista, użyj narzędzia Netsh.exe, które jest już zainstalowane.
  
> [!NOTE]
> Modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.  
  
## <a name="determine-how-ports-are-configured"></a>Określanie sposobu konfigurowania portów  
  
1. W systemie Windows Server 2003 lub Windows XP użyj narzędzia HttpCfg.exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **kwerendy** i **przełączników Ssl,** jak pokazano w poniższym przykładzie.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. W systemie Windows Vista użyj narzędzia Netsh.exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Pobierz odcisk palca certyfikatu  
  
1. Użyj przystawki Mmc certyfikatów, aby znaleźć certyfikat X.509, który ma zamierzony cel uwierzytelniania klienta. Aby uzyskać więcej informacji, zobacz [Jak: Wyświetlanie certyfikatów przy przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Dostęp do odcisku palca certyfikatu. Aby uzyskać więcej informacji, zobacz [Jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.  
  
4. Usuń wszystkie spacje między znakami szesnastkowymi. Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu i zastąpienie każdej spacji znakiem zerowym.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>Powiąż certyfikat SSL z numerem portu  
  
1. W systemie Windows Server 2003 lub Windows XP użyj narzędzia HttpCfg.exe w trybie "set" w magazynie SSL (Secure Sockets Layer) w celu powiązania certyfikatu z numerem portu. Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Przełącznik **-i** ma składnię `IP``port` : i nakazuje narzędziu ustawienie certyfikatu na port 8012 komputera. Opcjonalnie cztery zera, które poprzedzają numer, można również zastąpić rzeczywistym adresem IP komputera.  
  
    - Przełącznik **-h** określa odcisk palca certyfikatu.  
  
2. W systemie Windows Vista użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - Parametr **certhash** określa odcisk palca certyfikatu.  
  
    - Parametr **ipport** określa adres IP i port oraz działa podobnie jak przełącznik **-i** opisanego narzędzia Httpcfg.exe.  
  
    - Parametr **appid** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji posiadającej.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Powiąż certyfikat SSL z numerem portu i certyfikatami klientów pomocy technicznej  
  
1. W systemie Windows Server 2003 lub Windows XP, aby obsługiwać klientów uwierzytelniających się za pomocą certyfikatów X.509 w warstwie transportu, wykonaj poprzednią procedurę, ale przekaż dodatkowy parametr wiersza polecenia do programu HttpCfg.exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Przełącznik **-f** ma składnię, `n` gdzie n jest liczbą z 1 a 7. Wartość 2, jak pokazano w poprzednim przykładzie, włącza certyfikaty klienta w warstwie transportu. Wartość 3 umożliwia certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows. Zobacz HttpCfg.exe Pomoc dla zachowania innych wartości.  
  
2. W systemie Windows Vista, aby obsługiwać klientów uwierzytelniających się za pomocą certyfikatów X.509 w warstwie transportu, wykonaj poprzednią procedurę, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Usuwanie certyfikatu SSL z numeru portu  
  
1. Użyj narzędzia HttpCfg.exe lub Netsh.exe, aby wyświetlić porty i odciski palców wszystkich powiązań na komputerze. Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. W systemie Windows Server 2003 lub Windows XP użyj narzędzia HttpCfg.exe ze słowami kluczowymi **delete** i **ssl.** Użyj przełącznika **-i,** aby określić `IP`:`port` liczbę i przełącznik **-h,** aby określić odcisk palca.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. W systemie Windows Vista użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Przykład  

 Poniższy kod pokazuje, jak utworzyć usługę hostowane samodzielnie przy użyciu zestawu <xref:System.ServiceModel.WSHttpBinding> klas do zabezpieczeń transportu. Podczas tworzenia aplikacji należy określić numer portu w adresie.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
