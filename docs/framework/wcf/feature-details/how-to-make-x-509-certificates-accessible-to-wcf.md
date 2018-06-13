---
title: 'Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- X.509 certificates [WCF]
- certificates [WCF], making X.509 certificates accessible to WCF
- X.509 certificates [WCF], making accessible to WCF
ms.assetid: a54e407c-c2b5-4319-a648-60e43413664b
ms.openlocfilehash: cd13eae0a72ceaf5abfb93dfe84a53cfc3c8dec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493709"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF
Aby udostępnić certyfikat X.509 do usługi Windows Communication Foundation (WCF), kod aplikacji należy określić nazwę magazynu certyfikatów i lokalizacji. W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509. Aby uzyskać klucz prywatny skojarzony z certyfikatem X.509 w magazynie certyfikatów, WCF musi mieć uprawnienia, aby to zrobić. Domyślnie tylko właściciel i konta System można uzyskać dostępu do klucza prywatnego certyfikatu.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Aby Udostępnianie certyfikatów X.509 w architekturze WCF  
  
1.  Nadaj kontu, które WCF działa dostęp do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509.  
  
    1.  Sprawdź, czy WCF wymaga dostęp do odczytu do klucza prywatnego dla certyfikatu X.509.  
  
         Poniższa tabela zawiera szczegóły, czy klucz prywatny musi być dostępny w przypadku używania certyfikatu X.509.  
  
        |Użyj certyfikatu X.509|klucz prywatny|  
        |---------------------------|-----------------|  
        |Cyfrowego podpisywania wychodzących wiadomości protokołu SOAP.|Tak|  
        |Sprawdzanie podpisu dla ruchu przychodzącego komunikatu protokołu SOAP.|Nie|  
        |Szyfrowanie wiadomości wychodzącej protokołu SOAP.|Nie|  
        |Odszyfrowywanie przychodzącego komunikatu protokołu SOAP.|Tak|  
  
    2.  Ustal lokalizacja magazynu certyfikatów i nazwy, w którym przechowywany jest certyfikat.  
  
         Magazyn certyfikatów, w którym znajduje się certyfikat jest określona w kodzie aplikacji lub w konfiguracji. Na przykład w poniższym przykładzie określa, że certyfikat znajduje się w `CurrentUser` magazynie certyfikatów o nazwie `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3.  Określić lokalizację klucza prywatnego dla certyfikatu na komputerze przy użyciu [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzia.  
  
         [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzie wymaga nazwę magazynu certyfikatów, lokalizacja magazynu certyfikatów i coś, który unikatowo identyfikuje certyfikatu. Narzędzie akceptuje nazwa podmiotu certyfikatu lub jego odcisk palca jako unikatowy identyfikator. Aby uzyskać więcej informacji dotyczących sposobu ustalenia odcisku palca certyfikatu, zobacz [porady: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Poniższy przykład kodu wykorzystuje [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzia, aby określić lokalizację klucza prywatnego dla certyfikatu w `My` przechowywać w `CurrentUser` z odciskiem palca `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```  
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4.  Określ konto, na którym uruchomiony jest WCF.  
  
         Poniższa tabela zawiera szczegóły konta, na którym uruchomiono usługi WCF w danym scenariuszu.  
  
        |Scenariusz|Tożsamość procesu|  
        |--------------|----------------------|  
        |Klient (konsoli lub aplikacja WinForms).|Aktualnie zalogowanego użytkownika.|  
        |Usługa, która jest samodzielnie hostowana.|Aktualnie zalogowanego użytkownika.|  
        |Usługa, która znajduje się w usługach IIS 6.0 ([!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]) lub usług IIS 7.0 ([!INCLUDE[wv](../../../../includes/wv-md.md)]).|USŁUGA SIECIOWA|  
        |Oznacza to usługi hostowanej w usługach IIS 5.X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Steruje `<processModel>` elementu w pliku Machine.config. Domyślne konto jest ASPNET.|  
  
    5.  Przyznać dostęp do odczytu do pliku, który zawiera klucz prywatny, aby konto usługi WCF jest uruchomiona w ramach, przy użyciu narzędzia, takiego jak cacls.exe.  
  
         Poniższy kod przykładowy edycji (/ E) listy kontroli dostępu (ACL) dla określonego pliku udzielić (/ G) odczytu konto Usługa sieciowa (: R) dostępu do pliku.  
  
        ```  
        cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Zobacz też  
 [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)  
 [Instrukcje: pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
