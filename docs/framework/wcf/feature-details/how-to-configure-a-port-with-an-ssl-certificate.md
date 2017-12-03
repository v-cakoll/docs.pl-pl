---
title: 'Instrukcje: Konfigurowanie portu z certyfikatem SSL'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc4d6e3bb20cbe005ad7ce21ed37fe57c5d3466b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Instrukcje: Konfigurowanie portu z certyfikatem SSL
Podczas tworzenia własnym hostowanej [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi z <xref:System.ServiceModel.WSHttpBinding> zabezpieczenia transportu używa klasy, należy również skonfigurować port za pomocą certyfikatu X.509. Jeśli nie utworzysz samodzielnie hostowana usługa, może obsługiwać usługi na Internet Information Services (IIS). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby skonfigurować port, narzędzia, których używasz zależy od systemu operacyjnego, który działa na tym komputerze.  
  
 Jeśli używasz [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe. Z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] to narzędzie jest zainstalowany. Z [!INCLUDE[wxp](../../../../includes/wxp-md.md)], możesz pobrać narzędzia z [narzędzia obsługi systemu Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=88606). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Omówienie tak](http://go.microsoft.com/fwlink/?LinkId=88605). [Dokumentacji narzędzia obsługi systemu Windows](http://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia Httpcfg.exe.  
  
 Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, która jest już zainstalowana.  
  
 W tym temacie opisano sposób wykonania kilku procedur:  
  
-   Określanie konfiguracji portu bieżącego komputera.  
  
-   Pobieranie odcisku palca certyfikatu (niezbędne do dwóch poniższych procedur).  
  
-   Powiązania certyfikatu SSL do konfiguracji portów.  
  
-   Powiązania certyfikatu SSL do konfiguracji portów i pomocnicze certyfikaty klienta.  
  
-   Usunięcie certyfikatu SSL z numeru portu.  
  
 Należy pamiętać, że zmodyfikowanie certyfikaty przechowywane na komputerze wymaga uprawnień administracyjnych.  
  
### <a name="to-determine-how-ports-are-configured"></a>Aby określić, jak skonfigurować porty  
  
1.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe, aby wyświetlić bieżącą konfigurację portu, przy użyciu **zapytania** i **ssl** zmienia, jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe Aby wyświetlić bieżącą konfigurację portów, jak pokazano w poniższym przykładzie.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Aby uzyskać odcisk palca certyfikatu  
  
1.  Użyj przystawki certyfikatów konsoli MMC można znaleźć certyfikatu X.509, który ma zamierzony cel uwierzytelniania klienta. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Dostęp do odcisk palca certyfikatu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3.  Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.  
  
4.  Usuń wszystkie spacje między znaków szesnastkowych. Co w tym celu należy korzystać z funkcji znajdowania i zamieniania edytora tekstowego i Zastąp każdego miejsca znak null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Aby powiązać certyfikatu SSL z numeru portu  
  
1.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe w trybie "set" w magazynie Secure Sockets Layer (SSL), aby powiązać certyfikat z numeru portu. Narzędzie używana odcisk palca certyfikatu, jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **-I** przełącznik ma składnię `IP`:`port` i powoduje, że narzędzie, aby ustawić certyfikat z portem 8012 komputera. Opcjonalnie cztery zera, które Poprzedź numer można również zastąpić rzeczywisty adres IP komputera.  
  
    -   **-H** przełącznik określa odcisk palca certyfikatu.  
  
2.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **Skrót certyfikatu** parametr określa odcisk palca certyfikatu.  
  
    -   **Ipport** parametr określa adres IP i port, a funkcje podobnie jak **-i** przełącznika narzędzia Httpcfg.exe opisem.  
  
    -   **Appid** parametru jest identyfikatorem GUID, który może służyć do identyfikowania będący właścicielem aplikacji.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Aby powiązać certyfikatu SSL z numeru portu i obsługują certyfikaty klientów  
  
1.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], do obsługi klientów, którzy uwierzytelniania za pomocą certyfikatów X.509 w przypadku warstwy transportu, wykonaj poprzednią procedurę, ale przekazać dodatkowy parametr wiersza polecenia do HttpCfg.exe, jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** przełącznik ma składnię `n` gdzie n jest liczbą z zakresu od 1 do 7. Wartość 2, jak pokazano w poprzednim przykładzie, włącza certyfikaty klienta w przypadku warstwy transportu. Wartość 3 umożliwia certyfikaty klienta i mapuje te certyfikaty, konto systemu Windows. Zapoznaj się z pomocą HttpCfg.exe zachowania innych wartości.  
  
2.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], do obsługi klientów, którzy uwierzytelniania za pomocą certyfikatów X.509 w przypadku warstwy transportu, wykonaj poprzednią procedurę, ale z parametrem dodatkowe, jak pokazano w poniższym przykładzie.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Aby usunąć certyfikat SSL z numeru portu  
  
1.  Użyj narzędzia HttpCfg.exe lub Netsh.exe zawiera portów i odciski palców wszystkie powiązania na komputerze. Aby wydrukować dane na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe z **usunąć** i **ssl** słów kluczowych. Użyj **-i** przełącznika `IP`:`port` numer i **-h** przełącznika do określania odcisku palca.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia hostowanie Samoobsługowe przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy ustawienia zabezpieczeń transportu. Podczas tworzenia aplikacji, należy określić numer portu w adresie.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
