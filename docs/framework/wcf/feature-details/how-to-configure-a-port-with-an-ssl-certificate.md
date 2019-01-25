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
ms.openlocfilehash: 3aa32e54643ffb8e2e4e40f730ab3f5c084b8cd9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521724"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Instrukcje: Konfigurowanie portu z certyfikatem SSL
Podczas tworzenia własnego usługi Windows Communication Foundation (WCF) z <xref:System.ServiceModel.WSHttpBinding> zabezpieczenia transportu używa klasy, należy również skonfigurować port, za pomocą certyfikatu X.509. Jeśli nie tworzysz własne usługi, możesz hostować usługi w Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby skonfigurować port, użyte narzędzie zależy od systemu operacyjnego, który jest uruchomiony na Twoim komputerze.  
  
 Jeśli używasz [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe. Za pomocą [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] to narzędzie jest instalowane. Za pomocą [!INCLUDE[wxp](../../../../includes/wxp-md.md)], możesz pobrać narzędzia z [narzędzia obsługi systemu Windows XP Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Aby uzyskać więcej informacji, zobacz [Przegląd tak](https://go.microsoft.com/fwlink/?LinkId=88605). [Dokumentację Windows Support Tools](https://go.microsoft.com/fwlink/?LinkId=94840) opisano składnię narzędzia Httpcfg.exe.  
  
 Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, która jest już zainstalowana.  
  
 W tym temacie opisano sposób wykonania kilku procedur:  
  
-   Określanie konfiguracji portu z bieżącego komputera.  
  
-   Pobieranie odcisku palca certyfikatu (wymagane dla dwóch poniższych procedur).  
  
-   Powiązanie certyfikatu SSL z konfiguracji portów.  
  
-   Powiązanie certyfikatu SSL z konfiguracji portów i obsługi certyfikatów klienta.  
  
-   Usuwanie certyfikatu SSL z numeru portu.  
  
 Należy pamiętać, że modyfikowanie certyfikaty przechowywane na komputerze wymaga uprawnień administracyjnych.  
  
### <a name="to-determine-how-ports-are-configured"></a>Aby określić, jak porty są skonfigurowane.  
  
1.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe do wyświetlenia bieżącej konfiguracji portów przy użyciu **zapytania** i **ssl** przełączy się, jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], należy użyć narzędzia Netsh.exe do wyświetlenia bieżącej konfiguracji portów, jak pokazano w poniższym przykładzie.  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Aby uzyskać odcisk palca certyfikatu  
  
1.  Użyj przystawki MMC certyfikatów, aby znaleźć certyfikat X.509, który ma zamierzony cel Uwierzytelnianie klienta. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Dostęp do odcisk palca certyfikatu. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3.  Skopiuj odcisk palca certyfikatu do edytora tekstów, takiego jak Notatnik.  
  
4.  Usuń wszystkie spacje między znaków szesnastkowych. Jednym ze sposobów osiągnięcia tego jest korzystać z funkcji znajdowania i zamieniania w edytorze tekstów i Zastąp każdą spację znakiem null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Aby powiązać certyfikatu SSL do numeru portu  
  
1.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe w trybie "set" w sklepie Secure Sockets Layer (SSL), aby powiązać certyfikat numeru portu. Narzędzie używana odcisk palca certyfikatu, jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   **-I** przełącznik ma składnię `IP`:`port` i powoduje, że narzędzie, aby ustawić certyfikat z portem 8012 komputera. Opcjonalnie cztery zera, które poprzedzają numer można również zastąpić rzeczywistego adresu IP komputera.  
  
    -   **-H** przełącznik określa odcisk palca certyfikatu.  
  
2.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   **Certhash** parametr określa odcisk palca certyfikatu.  
  
    -   **Ipport** parametr określa adres IP i port, a funkcje podobnie jak **-i** przełącznika narzędzia Httpcfg.exe opisem.  
  
    -   **Appid** parametru jest identyfikatorem GUID, który może służyć do identyfikowania będąca właścicielem aplikacji.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Powiąż certyfikat SSL na numer portu i obsługują certyfikaty klientów  
  
1.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], które obsługują klientów, którzy uwierzytelniania za pomocą certyfikatów X.509 w warstwie transportowej, wykonaj poprzednią procedurę, ale należy przekazać dodatkowy parametr wiersza polecenia do HttpCfg.exe, jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     **-F** przełącznik ma składnię `n` gdzie n to liczba od 1 do 7. Wartość 2, jak pokazano w powyższym przykładzie umożliwia certyfikaty klienta w warstwie transportowej. Wartość 3 umożliwia certyfikaty klienta i mapuje te certyfikaty do konta Windows. Zapoznaj się z pomocą HttpCfg.exe zachowania inne wartości.  
  
2.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], dla klientów pomocy technicznej, którzy uwierzytelniać za pomocą certyfikatów X.509 w warstwie transportowej, wykonaj poprzednią procedurę, ale o dodatkowy parametr, jak pokazano w poniższym przykładzie.  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Aby usunąć certyfikat SSL z numeru portu  
  
1.  Użyj narzędzia HttpCfg.exe lub Netsh.exe, aby zobaczyć porty i odciski palca wszystkie powiązania na komputerze. Aby wydrukować dane na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], użyj narzędzia HttpCfg.exe z **Usuń** i **ssl** słów kluczowych. Użyj **-i** przełącznika `IP`:`port` cyfrą i **-h** Przełącz się do określania odcisku palca.  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  W [!INCLUDE[wv](../../../../includes/wv-md.md)], użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod pokazuje, jak utworzyć samodzielnie hostowanej usługi za pomocą <xref:System.ServiceModel.WSHttpBinding> klasy ustawienie zabezpieczeń transportu. Podczas tworzenia aplikacji, należy określić numer portu w adresie.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
