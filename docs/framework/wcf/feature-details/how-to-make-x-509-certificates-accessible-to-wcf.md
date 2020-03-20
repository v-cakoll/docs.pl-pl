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
ms.openlocfilehash: 14f2242ab55795c74fa169382fef846bc0e60ace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184895"
---
# <a name="how-to-make-x509-certificates-accessible-to-wcf"></a>Instrukcje: Udostępnianie certyfikatów X.509 w architekturze WCF
Aby certyfikat X.509 był dostępny dla programu Windows Communication Foundation (WCF), kod aplikacji musi określać nazwę i lokalizację magazynu certyfikatów. W pewnych okolicznościach tożsamość procesu musi mieć dostęp do pliku zawierającego klucz prywatny skojarzony z certyfikatem X.509. Aby uzyskać klucz prywatny skojarzony z certyfikatem X.509 w magazynie certyfikatów, WCF musi mieć do tego uprawnienia. Domyślnie tylko właściciel i konto systemowe mogą uzyskać dostęp do klucza prywatnego certyfikatu.  
  
### <a name="to-make-x509-certificates-accessible-to-wcf"></a>Aby udostępnić certyfikaty X.509 WCF  
  
1. Podaj konto, na którym WCF jest uruchomiony dostęp do odczytu do pliku, który zawiera klucz prywatny skojarzony z certyfikatem X.509.  
  
    1. Określ, czy WCF wymaga dostępu do odczytu do klucza prywatnego dla certyfikatu X.509.  
  
         W poniższej tabeli opisano, czy klucz prywatny musi być dostępny podczas korzystania z certyfikatu X.509.  
  
        |Użycie certyfikatu X.509|Klucz prywatny|  
        |---------------------------|-----------------|  
        |Cyfrowe podpisywanie wychodzącej wiadomości SOAP.|Tak|  
        |Weryfikowanie podpisu przychodzącej wiadomości SOAP.|Nie|  
        |Szyfrowanie wychodzącej wiadomości SOAP.|Nie|  
        |Odszyfrowywanie przychodzącego komunikatu SOAP.|Tak|  
  
    2. Określ lokalizację magazynu certyfikatów i nazwę, w której certyfikat jest przechowywany.  
  
         Magazyn certyfikatów, w którym przechowywany jest certyfikat, jest określony w kodzie aplikacji lub w konfiguracji. Na przykład poniższy przykład określa, że certyfikat `CurrentUser` znajduje `My`się w magazynie certyfikatów o nazwie .  
  
         [!code-csharp[x509Accessible#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/x509accessible/cs/source.cs#1)]
         [!code-vb[x509Accessible#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/x509accessible/vb/source.vb#1)]  
  
    3. Określ, gdzie znajduje się klucz prywatny certyfikatu na komputerze za pomocą narzędzia [FindPrivateKey.](../../../../docs/framework/wcf/samples/findprivatekey.md)  
  
         Narzędzie [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) wymaga nazwy magazynu certyfikatów, lokalizacji magazynu certyfikatów i czegoś, co jednoznacznie identyfikuje certyfikat. Narzędzie akceptuje nazwę podmiotu certyfikatu lub jego odcisk palca jako unikatowy identyfikator. Aby uzyskać więcej informacji na temat określania odcisku palca certyfikatu, zobacz [Jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
         Poniższy przykład kodu używa [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md) narzędzie do określenia lokalizacji klucza `My` prywatnego `CurrentUser` dla certyfikatu `46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d`w magazynie w za pomocą odcisku palca .  
  
        ```console
        findprivatekey.exe My CurrentUser -t "46 dd 0e 7a ed 0b 7a 31 9b 02 a3 a0 43 7a d8 3f 60 40 92 9d" -a  
        ```  
  
    4. Określ konto, pod które działa WCF.  
  
         W poniższej tabeli opisano konto, na którym WCF jest uruchomiony dla danego scenariusza.  
  
        |Scenariusz|Tożsamość procesu|  
        |--------------|----------------------|  
        |Klienta (aplikacja konsoli lub WinForms).|Aktualnie zalogowany użytkownik.|  
        |Usługa, która jest hostowana samodzielnie.|Aktualnie zalogowany użytkownik.|  
        |Usługa hostowana w usługach IIS 6.0 (Windows Server 2003) lub IIS 7.0 (Windows Vista).|USŁUGA SIECIOWA|  
        |Usługa hostowana w usługach IIS 5.X (Windows XP).|Kontrolowane przez `<processModel>` element w pliku Machine.config. Domyślnym kontem jest ASPNET.|  
  
    5. Udziel dostępu do odczytu do pliku zawierającego klucz prywatny do konta, pod którym działa WCF, za pomocą narzędzia, takiego jak icacls.exe.  
  
         Poniższy przykład kodu edytuje uznaniową listę kontroli dostępu (DACL) dla określonego pliku, aby udzielić dostępu do pliku do odczytu (:R) konta USŁUGI SIECIowej.  
  
        ```console
        icacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /grant "NETWORK SERVICE":R  
        ```  
  
## <a name="see-also"></a>Zobacz też

- [FindPrivateKey](../../../../docs/framework/wcf/samples/findprivatekey.md)
- [Instrukcje: pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
