---
title: 'Instrukcje: konfigurowanie portu z certyfikatem SSL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 6e21311802b0a3ce4e415b14686b101d31f18035
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893313"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Instrukcje: konfigurowanie portu z certyfikatem SSL
Podczas tworzenia samohostowanej usługi Windows Communication Foundation (WCF) z <xref:System.ServiceModel.WSHttpBinding> klasą, która korzysta z zabezpieczeń transportu, należy również skonfigurować port za pomocą certyfikatu X. 509. Jeśli nie tworzysz usługi samodzielnej, możesz hostować usługę w Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego działającego na komputerze.  
  
 Jeśli używasz programu [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub,Użyj narzędzia HttpCfg. exe. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] Po [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] zainstalowaniu tego narzędzia. Za [!INCLUDE[wxp](../../../../includes/wxp-md.md)]pomocą narzędzia można pobrać narzędzie w [systemie Windows XP z dodatkiem Service Pack 2](https://go.microsoft.com/fwlink/?LinkId=88606). Aby uzyskać więcej informacji, zobacz [Httpcfg Overview (przegląd](https://go.microsoft.com/fwlink/?LinkId=88605)). [Dokumentacja narzędzi pomocy technicznej systemu Windows](https://go.microsoft.com/fwlink/?LinkId=94840) objaśnia składnię dla narzędzia HttpCfg. exe.  
  
 Jeśli używasz programu, użyj narzędzia Netsh. exe, które jest już zainstalowane. [!INCLUDE[wv](../../../../includes/wv-md.md)]  
  
 W tym temacie opisano sposób wykonywania kilku procedur:  
  
- Określanie bieżącej konfiguracji komputera.  
  
- Pobieranie odcisku palca certyfikatu (wymagane w przypadku poniższych dwóch procedur).  
  
- Powiązanie certyfikatu SSL z konfiguracją portu.  
  
- Powiązanie certyfikatu SSL z konfiguracją portu i obsługą certyfikatów klienta.  
  
- Usuwanie certyfikatu SSL z numeru portu.  
  
 Należy zauważyć, że modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.  
  
### <a name="to-determine-how-ports-are-configured"></a>Aby określić sposób konfiguracji portów  
  
1. W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] programie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub użyj narzędzia HttpCfg. exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **zapytań** i przełączników **SSL** , jak pokazano w poniższym przykładzie.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie Użyj narzędzia Netsh. exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a>Aby uzyskać odcisk palca certyfikatu  
  
1. Za pomocą przystawki MMC Certyfikaty Znajdź certyfikat X. 509, który ma zamierzony cel uwierzytelniania klientów. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów z przystawką](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)programu MMC.  
  
2. Uzyskaj dostęp do odcisku palca certyfikatu. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.  
  
4. Usuń wszystkie spacje między znakami szesnastkowymi. Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu oraz zastępowanie każdej spacji znakiem null.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a>Aby powiązać certyfikat protokołu SSL z numerem portu  
  
1. W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systemie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub użyj narzędzia HttpCfg. exe w trybie "Set" w magazynie SSL (SSL), aby powiązać certyfikat z numerem portu. Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Przełącznik **-i** ma składnię `IP`:`port` i instruuje narzędzie, aby ustawić certyfikat na port 8012 komputera. Opcjonalnie cztery zera, które poprzedzają liczbę, można również zastąpić rzeczywistym adresem IP komputera.  
  
    - Przełącznik **-h** określa odcisk palca certyfikatu.  
  
2. W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    - Parametr **certhash** określa odcisk palca certyfikatu.  
  
    - Parametr **IPPORT** określa adres IP i port oraz działa podobnie jak w **przypadku przełącznika Httpcfg** . exe opisanego w opisie.  
  
    - Identyfikator **AppID** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji będącej właścicielem.  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Aby powiązać certyfikat protokołu SSL z numerem portu i obsługiwać certyfikaty klienta  
  
1. W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] programie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub, aby obsługiwać klientów, którzy uwierzytelniają się za pomocą certyfikatów X. 509 w warstwie transportowej, postępuj zgodnie z powyższą procedurą, ale Przekaż dodatkowy parametr wiersza polecenia do HttpCfg. exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Przełącznik **-f** ma składnię, gdzie `n` n jest liczbą z zakresu od 1 do 7. Wartość 2, jak pokazano w powyższym przykładzie, umożliwia korzystanie z certyfikatów klienta w warstwie transportowej. Wartość 3 włącza certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows. Zapoznaj się z tematem zachowanie innych wartości w pomocy programu HttpCfg. exe.  
  
2. W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej postępuj zgodnie z poprzednią procedurą, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a>Aby usunąć certyfikat SSL z numeru portu  
  
1. Użyj narzędzia HttpCfg. exe lub netsh. exe, aby zobaczyć porty i odciski palców wszystkich powiązań na komputerze. Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] programie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]lub użyj narzędzia HttpCfg. exe ze słowami kluczowymi **delete** i **SSL** . Aby`IP`określićodciskpalca, należy **użyć przełącznika** **-i.** `port`  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. W [!INCLUDE[wv](../../../../includes/wv-md.md)]programie Użyj narzędzia Netsh. exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia sposób tworzenia usługi samodzielnej przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy ustawionej na zabezpieczenia transportu. Podczas tworzenia aplikacji należy określić numer portu w adresie.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
