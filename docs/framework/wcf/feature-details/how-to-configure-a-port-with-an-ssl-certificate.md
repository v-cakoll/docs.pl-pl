---
title: 'Instrukcje: Konfigurowanie portu z certyfikatem SSL'
description: Dowiedz się, jak skonfigurować port za pomocą certyfikatu X. 509, który jest wymagany w przypadku samodzielnej usługi WCF z klasą WSHttpBinding za pomocą zabezpieczeń transportu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 0eccdf916dae7b886cbc4e6563e6dfe17039c321
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247185"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a>Instrukcje: Konfigurowanie portu z certyfikatem SSL

Podczas tworzenia samohostowanej usługi Windows Communication Foundation (WCF) z <xref:System.ServiceModel.WSHttpBinding> klasą, która korzysta z zabezpieczeń transportu, należy również skonfigurować port za pomocą certyfikatu X. 509. Jeśli nie tworzysz usługi samodzielnej, możesz hostować usługę w Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [zabezpieczenia transportu HTTP](http-transport-security.md).  
  
 Aby skonfigurować port, używane narzędzie zależy od systemu operacyjnego działającego na komputerze.  
  
 Jeśli korzystasz z systemu Windows Server 2003, użyj narzędzia HttpCfg.exe. W systemie Windows Server 2003 to narzędzie jest zainstalowane. Aby uzyskać więcej informacji, zobacz [Httpcfg Overview (przegląd](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))). [Dokumentacja narzędzi pomocy technicznej systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) objaśnia składnię narzędzia Httpcfg.exe.  
  
 Jeśli korzystasz z systemu Windows Vista, użyj narzędzia Netsh.exe, które jest już zainstalowane.
  
> [!NOTE]
> Modyfikowanie certyfikatów przechowywanych na komputerze wymaga uprawnień administracyjnych.  
  
## <a name="determine-how-ports-are-configured"></a>Określanie sposobu konfiguracji portów  
  
1. W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg.exe, aby wyświetlić bieżącą konfigurację portu przy użyciu **zapytań** i przełączników **SSL** , jak pokazano w poniższym przykładzie.  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. W systemie Windows Vista Użyj narzędzia Netsh.exe, aby wyświetlić bieżącą konfigurację portu, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a>Pobieranie odcisku palca certyfikatu  
  
1. Za pomocą przystawki MMC Certyfikaty Znajdź certyfikat X. 509, który ma zamierzony cel uwierzytelniania klientów. Aby uzyskać więcej informacji, zobacz [How to: View Certificates za pomocą przystawki MMC](how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2. Uzyskaj dostęp do odcisku palca certyfikatu. Aby uzyskać więcej informacji, zobacz [How to: Pobieranie odcisku palca certyfikatu](how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
3. Skopiuj odcisk palca certyfikatu do edytora tekstu, takiego jak Notatnik.  
  
4. Usuń wszystkie spacje między znakami szesnastkowymi. Jednym ze sposobów osiągnięcia tego celu jest użycie funkcji znajdowania i zamieniania edytora tekstu oraz zastępowanie każdej spacji znakiem null.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a>Powiąż certyfikat SSL z numerem portu  
  
1. W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg.exe w trybie "Set" w magazynie SSL (SSL), aby powiązać certyfikat z numerem portu. Narzędzie używa odcisku palca do identyfikowania certyfikatu, jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - Przełącznik **-i** ma składnię `IP` : `port` i instruuje narzędzie, aby ustawić certyfikat na port 8012 komputera. Opcjonalnie cztery zera, które poprzedzają liczbę, można również zastąpić rzeczywistym adresem IP komputera.  
  
    - Przełącznik **-h** określa odcisk palca certyfikatu.  
  
2. W systemie Windows Vista Użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - Parametr **certhash** określa odcisk palca certyfikatu.  
  
    - Parametr **IPPORT** określa adres IP i port oraz działa podobnie jak w **przypadku przełącznika Httpcfg.exe opisanego w** opisie narzędzia.  
  
    - Identyfikator **AppID** jest identyfikatorem GUID, który może służyć do identyfikowania aplikacji będącej właścicielem.  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a>Powiąż certyfikat SSL z numerem portu i obsługuj certyfikaty klienta  
  
1. W systemie Windows Server 2003 lub Windows XP w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej Wykonaj poprzednią procedurę, ale Przekaż dodatkowy parametr wiersza polecenia do HttpCfg.exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     Przełącznik **-f** ma składnię, `n` gdzie n jest liczbą z zakresu od 1 do 7. Wartość 2, jak pokazano w powyższym przykładzie, umożliwia korzystanie z certyfikatów klienta w warstwie transportowej. Wartość 3 włącza certyfikaty klienta i mapuje te certyfikaty na konto systemu Windows. Zobacz HttpCfg.exe pomoc dotyczącą zachowania innych wartości.  
  
2. W systemie Windows Vista w celu obsługi klientów uwierzytelnianych za pomocą certyfikatów X. 509 w warstwie transportowej Wykonaj poprzednią procedurę, ale z dodatkowym parametrem, jak pokazano w poniższym przykładzie.  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a>Usuwanie certyfikatu SSL z numeru portu  
  
1. Użyj narzędzia HttpCfg.exe lub Netsh.exe, aby zobaczyć porty i odciski palców wszystkich powiązań na komputerze. Aby wydrukować informacje na dysku, użyj znaku przekierowania ">", jak pokazano w poniższym przykładzie.  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. W systemie Windows Server 2003 lub Windows XP Użyj narzędzia HttpCfg.exe ze słowami kluczowymi **delete** i **SSL** . Aby określić **-i** `IP` `port` odcisk palca, należy **użyć przełącznika** -i.  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. W systemie Windows Vista Użyj narzędzia Netsh.exe, jak pokazano w poniższym przykładzie.  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a>Przykład  

 Poniższy kod przedstawia sposób tworzenia usługi samodzielnej przy użyciu <xref:System.ServiceModel.WSHttpBinding> klasy ustawionej na zabezpieczenia transportu. Podczas tworzenia aplikacji należy określić numer portu w adresie.  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia transportu HTTP](http-transport-security.md)
