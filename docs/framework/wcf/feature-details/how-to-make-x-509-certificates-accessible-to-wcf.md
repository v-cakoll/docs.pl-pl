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
ms.openlocfilehash: 7f24966f06730e62ea7a8967c3930f05ca78f50e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347082"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF
Aby udostępnić certyfikat X. 509 dla Windows Communication Foundation (WCF), kod aplikacji musi określać nazwę i lokalizację magazynu certyfikatów. W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X. 509. Aby uzyskać klucz prywatny skojarzony z certyfikatem X. 509 w magazynie certyfikatów, WCF musi mieć odpowiednie uprawnienia. Domyślnie tylko właściciel i konto systemowe mogą uzyskać dostęp do klucza prywatnego certyfikatu.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Aby udostępnić certyfikaty X. 509 dla usługi WCF  
  
1. Podaj konto, na którym działa funkcja WCF z dostępem do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X. 509.  
  
    1. Ustal, czy funkcja WCF wymaga dostępu do odczytu do klucza prywatnego dla certyfikatu X. 509.  
  
         W poniższej tabeli przedstawiono informacje o tym, czy klucz prywatny musi być dostępny podczas korzystania z certyfikatu X. 509.  
  
        |Użycie certyfikatu X. 509|Klucz prywatny|  
        |---------------------------|-----------------|  
        |Cyfrowe podpisywanie wychodzącego komunikatu protokołu SOAP.|Tak|  
        |Weryfikowanie podpisu przychodzącego komunikatu protokołu SOAP.|Nie|  
        |Szyfrowanie wychodzącego komunikatu protokołu SOAP.|Nie|  
        |Odszyfrowywanie przychodzącego komunikatu protokołu SOAP.|Tak|  
  
    2. Określ lokalizację i nazwę magazynu certyfikatów, w którym przechowywany jest certyfikat.  
  
         Magazyn certyfikatów, w którym jest przechowywany certyfikat, jest określany w kodzie aplikacji lub w konfiguracji. Na przykład poniższy przykład określa, że certyfikat znajduje się w `CurrentUser` magazyn certyfikatów o nazwie `My`.  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Określ, gdzie klucz prywatny certyfikatu znajduje się na komputerze przy użyciu narzędzia [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) .  
  
         Narzędzie [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) wymaga nazwy magazynu certyfikatów, lokalizacji magazynu certyfikatów i elementu, który jednoznacznie identyfikuje certyfikat. Narzędzie akceptuje nazwę podmiotu lub odcisk palca certyfikatu jako unikatowy identyfikator. Aby uzyskać więcej informacji na temat sposobu ustalania odcisku palca certyfikatu, zobacz [How to: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Poniższy przykład kodu używa narzędzia [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) do określenia lokalizacji klucza prywatnego certyfikatu w magazynie `My` w `CurrentUser` z odciskiem palca `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`.  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Określ konto, w ramach którego działa usługa WCF.  
  
         W poniższej tabeli przedstawiono szczegółowe informacje na temat konta, pod którym działa usługa WCF w danym scenariuszu.  
  
        |Scenariusz|Tożsamość procesu|  
        |--------------|----------------------|  
        |Klient (Aplikacja konsolowa lub WinForms).|Aktualnie zalogowany użytkownik.|  
        |Usługa, która jest samodzielna.|Aktualnie zalogowany użytkownik.|  
        |Usługa hostowana w usługach IIS 6,0 (Windows Server 2003) lub IIS 7,0 (Windows Vista).|USŁUGA SIECIOWA|  
        |Usługa hostowana w usługach IIS 5. X ([!INCLUDE[wxp](../../../../includes/wxp-md.md)]).|Kontrolowane przez element `<processModel>` w pliku Machine. config. Domyślne konto to ASPNET.|  
  
    5. Przyznaj uprawnienia do odczytu pliku, który zawiera klucz prywatny do konta, w ramach którego działa usługa WCF, przy użyciu narzędzia, takiego jak icacls. exe.  
  
         Poniższy przykład kodu umożliwia edycję poufnej listy kontroli dostępu (DACL) dla określonego pliku, aby przyznać kontu usługi sieciowej odczytywanie (: R) dostępu do pliku.  
  
        ```console 
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Zobacz także

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Instrukcje: pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
