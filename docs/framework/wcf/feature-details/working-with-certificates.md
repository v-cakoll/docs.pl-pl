---
title: Praca z certyfikatami
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
helpviewer_keywords: certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63f9d22c571a007653fc794dc7638c8221a676aa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="working-with-certificates"></a>Praca z certyfikatami
Aby program [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zabezpieczeń, X.509 certyfikaty cyfrowe są często używane do uwierzytelniania klientów i serwerów, szyfrowania i cyfrowego podpisywania wiadomości. Ten temat zawiera krótkie opisy X.509 certyfikatu cyfrowego funkcji i sposobie korzystania z nich w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oraz linki do tematów, które opisano te pojęcia dalsze lub które pokazują, jak wykonywać typowe zadania za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i certyfikatów.  
  
 Krótko mówiąc, certyfikat jest częścią *infrastruktury kluczy publicznych* (PKI), która jest system certyfikaty cyfrowe, urzędy certyfikacji i innych urzędów rejestracji, sprawdź, które uwierzytelniają każdej Strony biorącej udział w operacji elektronicznej za pomocą kryptografii klucza publicznego. Urząd certyfikacji wystawia certyfikaty i każdy certyfikat ma zestaw pól, które zawierają dane, takie jak *podmiotu* (do której certyfikat został wystawiony jednostek), dat ważności (gdy certyfikat jest nieprawidłowy), wystawcy ( jednostki, który wystawił certyfikat), a klucz publiczny. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], każdej z tych właściwości jest przetwarzany jako <xref:System.IdentityModel.Claims.Claim>, a każde oświadczenie podzielić na dwa typy: tożsamość i w prawo. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Certyfikaty X.509 zobacz [certyfikatów kluczy publicznych X.509](http://go.microsoft.com/fwlink/?LinkId=209952) [!INCLUDE[crabout](../../../../includes/crabout-md.md)] oświadczeniami i autoryzacją w programie WCF, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Wdrażanie infrastruktury kluczy publicznych, zobacz [systemu Windows Server 2008 R2 — usługi certyfikatów](http://go.microsoft.com/fwlink/?LinkId=209949).  
  
 Podstawową funkcją certyfikat jest uwierzytelnianie tożsamość właściciela certyfikatu do innych użytkowników. Certyfikat zawiera *klucz publiczny* właściciela, gdy właściciel zachowuje klucza prywatnego. Klucz publiczny może służyć do szyfrowania wiadomości wysyłane do właściciela certyfikatu. Tylko właściciel ma dostęp do klucza prywatnego tak tylko właściciel może odszyfrować te wiadomości.  
  
 Certyfikaty muszą być wystawiane przez urząd certyfikacji, który jest często wystawcy certyfikatów innych firm. W domenie systemu Windows jest dołączony urząd certyfikacji który może służyć do wystawiania certyfikatów dla komputerów w domenie.  
  
## <a name="viewing-certificates"></a>Wyświetlanie certyfikatów  
 Aby pracować z certyfikatów, często jest niezbędne do ich wyświetlania i sprawdź, czy ich właściwości. Łatwo to zrobić za pomocą narzędzia przystawki programu Microsoft Management Console (MMC). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: wyświetlanie certyfikatów w przystawce programu MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Magazyny certyfikatów  
 Znaleziono w magazynach certyfikatów. Istnieją dwóch lokalizacji magazynu głównych, które są podzielone na magazyny podrzędne. Jeśli jesteś administratorem na komputerze, za pomocą przystawki programu MMC narzędzia można wyświetlić zarówno magazynów głównych. Użytkownicy inni niż administratorzy mogą wyświetlać tylko bieżący magazyn użytkownika.  
  
-   **Magazynu na komputerze lokalnym**. Zawiera certyfikaty używane przez procesy maszyny, takich jak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Użyj tej lokalizacji do przechowywania certyfikatów uwierzytelniania serwera wobec klientów.  
  
-   **Bieżący magazyn użytkownika**. Aplikacji zwykle umieścić tutaj certyfikatów dla bieżącego użytkownika komputera. W przypadku tworzenia aplikacji klienckiej, to zwykle umieszczane są certyfikaty, które przeprowadzają uwierzytelnianie użytkowników do usługi.  
  
 Tych dwóch magazynów są podzielone na magazyny podrzędnych. Najbardziej ważne tych programowania z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obejmują:  
  
-   **Zaufane główne urzędy certyfikacji**. Certyfikaty można użyć w tym magazynie, można utworzyć łańcucha certyfikatów, które można prześledzić do certyfikatu urzędu certyfikacji, w tym magazynie.  
  
    > [!IMPORTANT]
    >  Nawet, jeśli certyfikat nie pochodzi z urzędu certyfikacji innych firm zaufanego komputera lokalnego domyślnie ufa dowolny certyfikat umieszczane w tym magazynie. Z tego powodu nie umieszczaj dowolny certyfikat do tego magazynu chyba, że w pełni zaufania wystawca i zrozumienia konsekwencji tego działania.  
  
-   **Osobiste**. Ten magazyn jest używany dla certyfikatów skojarzonych z użytkownikiem komputera. Ten magazyn jest zazwyczaj używana w przypadku certyfikatów wystawianych przez jeden z certyfikatów urzędów certyfikacji w magazynie zaufanych głównych urzędów certyfikacji. Można również znaleźć tutaj certyfikatu mogą być własnym wystawiony i zaufany przez aplikację.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]magazyny certyfikatów, zobacz [magazynów certyfikatów](http://go.microsoft.com/fwlink/?LinkId=88912).  
  
### <a name="selecting-a-store"></a>Wybieranie magazynu  
 Wybieranie miejsce przechowywania certyfikatu zależy od sposobu i czasu uruchamia usługi lub klienta. Mają zastosowanie następujące reguły ogólne:  
  
-   Jeśli usługa WCF jest hostowana użycie usługi Windows **komputera lokalnego** przechowywania. Należy pamiętać, że wymagane są uprawnienia administratora, aby zainstalować certyfikaty w magazynie komputera lokalnego.  
  
-   Jeśli usługi lub klienta aplikację, która działa na koncie użytkownika, należy zastosować **bieżącego użytkownika** przechowywania.  
  
### <a name="accessing-stores"></a>Uzyskiwanie dostępu do magazynów  
 Magazyny są chronione przez listy kontroli dostępu (ACL), podobnie jak folderów na komputerze. Podczas tworzenia usługi hostowanej przez Internetowe usługi informacyjne (IIS), [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] proces jest uruchamiany w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] konta. Konto musi mieć dostęp do magazynu, który zawiera certyfikaty używane przez usługę. Każdy magazynów głównych jest chroniony za pomocą domyślnej listy dostępu, ale można zmodyfikować listy. Jeśli tworzysz oddzielne roli dostępu do magazynu, należy przyznać uprawnienia dostępu do tej roli. Aby dowiedzieć się, jak można zmodyfikować listy dostępu za pomocą narzędzia WinHttpCertConfig.exe, zobacz [porady: Tworzenie certyfikatów tymczasowych do użycia podczas tworzenia](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]przy użyciu certyfikatów klienta z usług IIS, zobacz [sposób wywoływania usługi sieci Web za pomocą certyfikatu klienta do uwierzytelniania w aplikacji sieci Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Łańcuch zaufania i urzędów certyfikacji  
 Certyfikaty są tworzone w hierarchii, w którym każdy certyfikat jest połączony z urzędu certyfikacji, który wystawił certyfikat. Jest to łącze do certyfikatu urzędu certyfikacji. Urząd certyfikacji certyfikatu, a następnie łączy do urzędu certyfikacji, który wystawił certyfikat oryginalnego urzędu certyfikacji. Ten proces jest powtarzany, dopóki certyfikat głównego urzędu certyfikacji zostanie osiągnięty. Certyfikat głównego urzędu certyfikacji jest dodatkowo z natury zaufanych.  
  
 Certyfikaty cyfrowe są używane do uwierzytelniania jednostki, korzystając z tej hierarchii, nazywany również *łańcuch zaufania*. Możesz wyświetlić łańcuch dowolny certyfikat za pomocą przystawki programu MMC dwukrotnie dowolny certyfikat, a następnie klikając **ścieżka certyfikatu** kartę [!INCLUDE[crabout](../../../../includes/crabout-md.md)] importowanie łańcuchów certyfikatów dla urzędu certyfikacji, zobacz [Porady: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Dowolnego wystawcy może pełnić zaufany główny urząd umieszczając wystawcę certyfikatu w magazynie certyfikatów zaufanego głównego urzędu.  
  
### <a name="disabling-chain-trust"></a>Wyłączanie łańcuch zaufania  
 Podczas tworzenia nowej usługi, używasz certyfikatu, który nie jest wystawiany przez zaufanego certyfikatu głównego lub nie można sam certyfikat wystawiającego certyfikaty w magazynie zaufanych głównych urzędów certyfikacji. Tylko do celów programistycznych można tymczasowo wyłączyć mechanizm, który sprawdza łańcuch zaufania certyfikatów. Aby to zrobić, ustaw `CertificateValidationMode` właściwości albo `PeerTrust` lub `PeerOrChainTrust`. Trybie Określa, że certyfikat można albo samodzielnie wystawiony (relacja zaufania elementów równorzędnych) lub jej część łańcuch zaufania. Można ustawić właściwości na dowolnym z następujących klas.  
  
|Class|Właściwość|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Można również ustawić właściwość za pomocą konfiguracji. Następujące elementy są używane do określania tryb walidacji:  
  
-   [\<Uwierzytelnianie >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Niestandardowe uwierzytelnianie  
 `CertificateValidationMode` Właściwości umożliwia również dostosować sposób uwierzytelniania certyfikatów. Domyślnie po ustawieniu poziomu `ChainTrust`. Aby użyć <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> wartości, należy także ustawić `CustomCertificateValidatorType` atrybutu zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć niestandardowego modułu weryfikacji, musi dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.  
  
 Podczas tworzenia niestandardowego wystawcy uwierzytelnienia, najważniejsze metody do przesłonięcia jest <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody. Na przykład niestandardowe uwierzytelnianie Zobacz [moduł weryfikacji certyfikatów X.509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) próbki. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Niestandardowe poświadczenia i weryfikacja poświadczeń](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-makecertexe-to-build-a-certificate-chain"></a>Przy użyciu Makecert.exe można utworzyć łańcucha certyfikatu  
 Narzędzie tworzenia certyfikatów (Makecert.exe) tworzy certyfikaty X.509 i prywatnego klucza publicznego i pary kluczy. Można zapisać klucza prywatnego na dysku, a następnie użyć go do wystawiania i zarejestrować nowe certyfikaty, w związku z tym symulując hierarchii certyfikatów łańcuchowych. To narzędzie jest przeznaczone do użytku wyłącznie jako pomoc podczas opracowywania usługi i nie mogą być używane w celu utworzenia certyfikatów do rzeczywistego wdrożenia. Podczas tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, wykonaj następujące kroki, aby utworzyć łańcuch zaufania z Makecert.exe.  
  
#### <a name="to-build-a-chain-of-trust-with-makecertexe"></a>Aby utworzyć łańcuch zaufania z Makecert.exe  
  
1.  Tworzenie tymczasowych głównego urzędu () certyfikatu z podpisem własnym za pomocą narzędzia MakeCert.exe. Zapisz klucz prywatny na dysku.  
  
2.  Użyj nowego certyfikatu do wystawienia innego certyfikatu, który zawiera klucz publiczny.  
  
3.  Zaimportuj certyfikat głównego urzędu certyfikacji w magazynie zaufanych głównych urzędów certyfikacji.  
  
4.  Aby uzyskać instrukcje, zobacz [porady: Tworzenie certyfikatów tymczasowych do użycia podczas tworzenia](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Certyfikat, który można używać?  
 Często zadawane pytania dotyczące certyfikatów są używane, który certyfikat i dlaczego. Odpowiedź zależy od tego, czy programowania klienta lub usługę. Poniższe informacje przedstawiono ogólne wskazówki i nie jest kompletną odpowiedzi na te pytania.  
  
### <a name="service-certificates"></a>Usługi certyfikatów  
 Usługi certyfikatów zostały zadania podstawowego uwierzytelniania serwera wobec klientów. Jednym z początkowej kontroli, gdy klient uwierzytelnia serwer jest porównanie wartości **podmiotu** pole do jednolity identyfikator zasobów (URI) używane do kontaktu z usługą: DNS oba muszą być zgodne. Na przykład, jeśli identyfikator URI usługi jest "http://www.contoso.com/endpoint/", a następnie **podmiotu** pole musi zawierać także wartość "www.contoso.com".  
  
 Należy pamiętać, że pole może zawierać kilka wartości każdego prefiksem inicjowania, aby wskazać wartość. Najczęściej inicjowania jest "CN" dla nazwy pospolitej, na przykład "CN = www.contoso.com". Istnieje również możliwość **podmiotu** pole jako pole pozostanie puste, w którym to przypadku **alternatywna nazwa podmiotu** pole może zawierać **nazwy DNS** wartość.  
  
 Należy również zauważyć wartość **zamierzone cele** pole certyfikatu powinna zawierać odpowiednią wartość, takie jak "Uwierzytelnianie serwera" lub "Uwierzytelnienie klienta".  
  
### <a name="client-certificates"></a>Certyfikaty klienta  
 Certyfikaty klienta nie są zwykle wystawiony przez urząd certyfikacji innych firm. Zamiast tego magazynu osobistego bieżącej lokalizacji użytkownika zazwyczaj zawiera certyfikaty umieszczone w nim przez urząd główny z przeznaczeniem "Uwierzytelnienie klienta". Klient może używać takich certyfikatów, gdy jest wymagane uwierzytelnianie wzajemne.  
  
## <a name="online-revocation-and-offline-revocation"></a>Odwołań w trybie online i Offline odwołania  
  
### <a name="certificate-validity"></a>Ważność certyfikatu  
 Każdy certyfikat jest prawidłowy tylko dla danego okresu czasu, nazywany *okres ważności*. Okres ważności jest definiowana za pomocą **ważny od** i **ważny do** pól certyfikatu X.509. Podczas uwierzytelniania certyfikat jest sprawdzany w celu ustalenia, czy certyfikat jest nadal w okresie ważności.  
  
### <a name="certificate-revocation-list"></a>Listy odwołania certyfikatów  
 W dowolnym momencie w okresie ważności urzędu certyfikacji można odwołać się do certyfikatu. Może to występować wielu powodów, takich jak złamania klucza prywatnego certyfikatu.  
  
 W takim przypadku sieciowych, co do których elementem podrzędnym elementu odwołanych certyfikatów również są nieprawidłowe i nie są zaufane podczas uwierzytelniania procedury. Aby dowiedzieć się, które certyfikaty są odwołane, Każdy wystawca publikuje, a data sygnaturą czasową *listy odwołania certyfikatów* (CRL). Listy można sprawdzić za pomocą odwołań w trybie online lub offline odwołania, ustawiając `RevocationMode` lub `DefaultRevocationMode` właściwości do jednej z następujących klas <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości wyliczenia: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> , a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasy. Wartość domyślna dla wszystkich właściwości to `Online`.  
  
 Można też ustawić tryb, w konfiguracji przy użyciu `revocationMode` atrybutu obu [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) i [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>Metoda SetCertificate  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], często należy określić certyfikat lub ustawić certyfikatów usługi lub klienta ma użyć do uwierzytelnienia, szyfrowania i cyfrowego podpisywania wiadomości. Można to zrobić programowo przy użyciu `SetCertificate` metody różnych klas, które reprezentują certyfikatów X.509. Następujące klasy użyj `SetCertificate` metodę, aby określić certyfikat.  
  
|Class|Metoda|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` Metoda polega na wyznaczenie lokalizacji magazynu i magazynu typu "Znajdź" (`x509FindType` parametru), który określa pole certyfikatu i wartość w polu. Na przykład poniższy kod tworzy <xref:System.ServiceModel.ServiceHost> wystąpienie i ustawia certyfikat usługi używany do uwierzytelniania usługi dla klientów z `SetCertificate` metody.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Wiele certyfikatów z tą samą wartością  
 Magazyn może zawierać wiele certyfikatów z taką samą nazwę podmiotu. Oznacza to, że jeśli użytkownik określi, że `x509FindType` jest <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> lub <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>i więcej niż jeden certyfikat ma taką samą wartość, jest zwracany wyjątek, becausethereisno sposób wyróżniania certyfikat, który jest wymagany. Można zaradzić przez ustawienie `x509FindType` do <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. W polu odcisku palca zawiera unikatową wartość, która może służyć do znaleźć określonego certyfikatu w magazynie. Jednak to ma własną wadą: Jeśli certyfikat jest odwołany lub odnowiony, `SetCertificate` metody zakończy się niepowodzeniem, ponieważ odcisk palca również został usunięty. Lub, jeśli certyfikat nie jest już prawidłowe, uwierzytelnianie nie powiedzie się. Aby temu zaradzić, należy ustawić `x590FindType` parametr <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> i określ nazwę wystawcy. Jeśli wymagana jest nie określonego wystawcę, można również ustawić jednego z innych <xref:System.Security.Cryptography.X509Certificates.X509FindType> wyliczenia wartości, takich jak <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Certyfikaty w konfiguracji  
 Certyfikaty można również ustawić za pomocą konfiguracji. W przypadku tworzenia usługi poświadczeń, takich jak certyfikaty, są określone w obszarze [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Klient są programowania, certyfikaty są określone w obszarze [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Mapowanie certyfikatu do konta użytkownika  
 Funkcja usług IIS i usługi Active Directory jest możliwość mapowania certyfikatu na konto użytkownika systemu Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]funkcji, zobacz [mapowania certyfikatów do kont użytkowników](http://go.microsoft.com/fwlink/?LinkId=88917).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]za pomocą mapowania usługi Active Directory, zobacz [mapowania certyfikatów klientów przy użyciu mapowanie usługi katalogowej](http://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Dzięki tej możliwości włączone, można ustawić <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> właściwość <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy do `true`. W konfiguracji, można ustawić `mapClientCertificateToWindowsAccount` atrybutu [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) elementu `true`, jak pokazano w poniższym kodzie.  
  
```xml  
<serviceBehaviors>  
 <behavior name="MappingBehavior">  
  <serviceCredentials>  
   <clientCertificate>  
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />  
   </clientCertificate>  
  </serviceCredentials>  
 </behavior>  
</serviceBehaviors>  
```  
  
 Mapowanie certyfikatu X.509 do tokenu, który reprezentuje konto użytkownika systemu Windows jest traktowane jako podniesienie uprawnień ponieważ zmapowaniu, token systemu Windows może służyć do uzyskania dostępu do chronionych zasobów. W związku z tym zasady domeny wymaga certyfikatu X.509 do wykonania jego zasad przed mapowania. *SChannel* pakiet zabezpieczeń wymusza to wymaganie.  
  
 Korzystając z [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszym, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia certyfikat spełnia zasady domeny przed jest mapowany na konto systemu Windows.  
  
 W pierwszej wersji programu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], mapowanie zostanie wykonane bez konsultacji zasad domeny. W związku z tym jest to możliwe, że starsze aplikacje, które używanej do pracy, gdy uruchomiona w ramach pierwszej wersji nie powiedzie się, jeśli włączono mapowania, a certyfikat X.509 nie spełnia zasad domeny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
