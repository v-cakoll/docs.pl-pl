---
title: 'Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ccbc8c6fa638c674dea28c312b2dedbc9d41968a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a>Instrukcje: Tworzenie certyfikatów tymczasowych do używania w trakcie opracowywania
Podczas tworzenia bezpiecznego usługi lub klienta przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], jest często przekazać certyfikat X.509 mają być używane jako poświadczenie. Certyfikat jest zwykle częścią łańcucha certyfikatów przy użyciu głównego urzędu został znaleziony w magazynie zaufanych głównych urzędów certyfikacji komputera. Posiadanie łańcuch certyfikatów umożliwia określania zakresu zestawu certyfikatów, w których zwykle głównego urzędu certyfikacji jest od swojej organizacji lub jednostki biznesowej. Aby emulować to w czasie tworzenia, możesz utworzyć dwa certyfikaty by spełnić ich wymagań zabezpieczeń. Pierwsza to certyfikatu z podpisem własnym, który jest umieszczony w magazynie zaufanych głównych urzędów certyfikacji i drugiego certyfikatu jest tworzona na podstawie pierwszego i znajduje się w magazynie osobistym lokalizacji komputera lokalnego lub w magazynie osobistym Bieżąca lokalizacja użytkownika. W tym temacie przedstawiono kroki, aby utworzyć tych dwóch certyfikatów przy użyciu [narzędzie tworzenia certyfikatów (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), które są dostarczane przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zestawu SDK.  
  
> [!IMPORTANT]
>  Narzędzie do tworzenia certyfikacji generuje certyfikaty są udostępniane tylko do celów testowych. Podczas wdrażania usługi lub klienta, należy użyć odpowiedni certyfikat dostarczony przez urząd certyfikacji. Może to być albo z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certyfikatów serwera w organizacji lub innych firm.  
>   
>  Domyślnie [Makecert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) tworzy certyfikaty, których główny urząd certyfikacji jest nazywany "Agencji głównego **."** Ponieważ agencję"główny" nie ma w magazynie zaufanych głównych urzędów certyfikacji, dzięki temu te certyfikaty niezabezpieczonych. Tworzenie certyfikatu z podpisem własnym, który znajduje się w zaufanych głównych urzędów certyfikacji magazynu umożliwia utworzenie Środowisko deweloperskie, która symuluje dokładniejsze środowiska wdrażania.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Tworzenie i używanie certyfikatów, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] za pomocą certyfikatu jako poświadczeń, zobacz [zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md). Samouczek dotyczący przy użyciu technologii Microsoft Authenticode, zobacz [Authenticode omówienia i samouczki](http://go.microsoft.com/fwlink/?LinkId=88919).  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a>Utwórz samopodpisany certyfikat głównego urzędu certyfikacji i eksportowanie klucza prywatnego  
  
1.  Za pomocą narzędzia MakeCert.exe z następujących parametrów:  
  
    1.  `-n` `subjectName`. Określa nazwę podmiotu. Konwencji jest przed nazwą podmiotu "CN =" dla "Nazwa pospolita".  
  
    2.  `-r`. Określa, że certyfikat będzie podpisem.  
  
    3.  `-sv` `privateKeyFile`. Określa plik, który zawiera kontener klucza prywatnego.  
  
     Na przykład następujące polecenie tworzy certyfikat z podpisem własnym z nazwą podmiotu "CN = TempCA."  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     Pojawi się monit o podanie hasła do ochrony klucza prywatnego. To hasło jest wymagane, gdy Tworzenie certyfikatu podpisanego przez ten certyfikat główny.  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a>Aby utworzyć nowy certyfikat podpisany przez certyfikat głównego urzędu certyfikacji  
  
1.  Za pomocą narzędzia MakeCert.exe z następujących parametrów:  
  
    1.  `-sk` `subjectKey`. Lokalizacja kontenera klucza podmiotu, który zawiera klucz prywatny. Jeśli kontener kluczy nie istnieje, zostanie utworzony jeden. Jeśli żadna z opcji -sk lub - sv jest używana, kontener klucza o nazwie JoeSoft zostanie utworzony domyślnie.  
  
    2.  `-n` `subjectName`. Określa nazwę podmiotu. Konwencji jest przed nazwą podmiotu "CN =" dla "Nazwa pospolita".  
  
    3.  `-iv` `issuerKeyFile`. Określa plik klucza prywatnego przez wystawcę.  
  
    4.  `-ic` `issuerCertFile`. Określa lokalizację wystawcy certyfikatu.  
  
     Na przykład następujące polecenie tworzy certyfikat z podpisem `TempCA` certyfikat głównego urzędu certyfikacji z nazwą podmiotu `"CN=SignedByCA"` przy użyciu klucza prywatnego wystawcy.  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a>Instalowanie certyfikatu w magazynie zaufanych urzędów certyfikacji głównego  
 Po utworzeniu certyfikatu z podpisem własnym można zainstalować go w magazynie zaufanych głównych urzędów certyfikacji. Wszystkie certyfikaty, które są podpisane przy użyciu certyfikatu w tym momencie są zaufane przez komputer. Z tego powodu należy usunąć certyfikat z magazynu jak nie są już potrzebne. Jeśli usuniesz ten certyfikat głównego urzędu certyfikacji, wszystkie certyfikaty, które podpisane z nim stają się nieautoryzowane. Certyfikaty urzędu głównego są po prostu mechanizm zgodnie z którymi grupy certyfikatów można ograniczyć zakres niezbędne. Na przykład w aplikacji peer-to-peer, nie ma zwykle nie jest konieczne urząd główny ponieważ tożsamość osoby po prostu zaufania przez podany certyfikat.  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a>Aby zainstalować certyfikat z podpisem własnym w zaufane główne urzędy certyfikacji  
  
1.  Otwórz przystawkę certyfikatu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
2.  Otwórz folder z certyfikatem, albo **komputera lokalnego** lub **bieżącego użytkownika**.  
  
3.  Otwórz **zaufane główne urzędy certyfikacji** folderu.  
  
4.  Kliknij prawym przyciskiem myszy **certyfikaty** folder i kliknij przycisk **wszystkie zadania**, następnie kliknij przycisk **importu**.  
  
5.  Postępuj zgodnie z wyświetlanymi na ekranie kreatora instrukcjami, aby zaimportować TempCa.cer magazynu.  
  
## <a name="using-certificates-with-wcf"></a>Za pomocą certyfikatów z programem WCF  
 Po skonfigurowaniu certyfikatów tymczasowych można używać ich do opracowywania rozwiązań WCF, które określają certyfikatów jako typu poświadczeń klienta. Na przykład następująca konfiguracja XML określa zabezpieczeń komunikatów i certyfikatu jako typu poświadczeń klienta.  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a>Aby określić certyfikat jako typu poświadczeń klienta  
  
-   W pliku konfiguracji dla usługi użyj następujący kod XML, aby ustawić trybu zabezpieczeń do wiadomości i typu poświadczeń klienta do certyfikatu.  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 W pliku konfiguracji dla klienta użyj następującego kodu XML, aby określić certyfikat został znaleziony w magazynie użytkownika czy można znaleźć, wyszukując pole SubjectName dla wartości "CohoWinery."  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 Aby uzyskać więcej informacji o używaniu certyfikatów w programie WCF, zobacz [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Pamiętaj usunąć wszystkie certyfikaty urzędu tymczasowego katalogu głównego z **zaufane główne urzędy certyfikacji** i **osobistych** folderów przez kliknięcie prawym przyciskiem myszy certyfikat, a następnie klikając polecenie  **Usuń**.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Instrukcje: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
