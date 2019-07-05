---
title: Praca z certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: 55d78ed9bf839d66b3487f91d71d7a07a2123c5f
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569553"
---
# <a name="working-with-certificates"></a>Praca z certyfikatami
Program Windows Communication Foundation (WCF) zabezpieczeń, certyfikaty cyfrowe X.509 często są używane do uwierzytelniania klientów i serwerów, szyfrowania i cyfrowego podpisywania wiadomości. W tym temacie krótko opisano funkcje cyfrowego certyfikatu X.509 oraz sposobu ich używania w programie WCF i zawiera łącza do tematów, opisano te pojęcia dalsze lub które pokazują sposób wykonywania typowych zadań przy użyciu programu WCF i certyfikatów.  
  
 Krótko mówiąc, certyfikatu cyfrowego jest częścią *infrastruktury kluczy publicznych* (PKI), czyli system certyfikaty cyfrowe, urzędy certyfikacji i innych urzędów rejestracji, sprawdź, które uwierzytelniają Każdy biorącego udział w transakcji elektronicznej za pomocą kryptografii klucza publicznego. Urząd certyfikacji wystawia certyfikaty, a każdy certyfikat ma zestaw pól, które zawierają dane, takie jak *podmiotu* (jednostka dla których wystawiono certyfikat), dat ważności (gdy certyfikat jest ważny), wystawcy ( obiekt, który wystawił certyfikat), a klucz publiczny. W programie WCF, każda z tych właściwości jest przetwarzany jako <xref:System.IdentityModel.Claims.Claim>, a każde oświadczenie jest podzielona na dwa typy: tożsamości i po prawej stronie. Aby uzyskać więcej informacji na temat X.509 certyfikatów Zobacz [klucz publiczny certyfikatu X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Aby uzyskać więcej informacji na temat oświadczeniami i autoryzacją w usłudze WCF zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md). Aby uzyskać więcej informacji na temat wdrażania infrastruktury kluczy publicznych, zobacz [infrastruktura PKI przedsiębiorstwa z systemem Windows Server 2012 R2 usługi certyfikatów Active Directory](https://blogs.technet.microsoft.com/yungchou/2013/10/21/enterprise-pki-with-windows-server-2012-r2-active-directory-certificate-services-part-1-of-2/).  
  
 Podstawową funkcją certyfikatu jest uwierzytelnianie tożsamość właściciela certyfikatu do innych osób. Certyfikat zawiera *klucza publicznego* właściciela, podczas gdy właściciela przechowuje klucz prywatny. Klucz publiczny może służyć do szyfrowania wiadomości wysyłane do właściciela certyfikatu. Tylko właściciel ma dostęp do klucza prywatnego, dlatego tylko właściciel może odszyfrować te komunikaty.  
  
 Certyfikaty muszą być wystawiane przez urząd certyfikacji, które są często wystawcy certyfikatów innych firm. Domenę Windows urzędu certyfikacji jest zainstalowana na które może służyć do wystawiania certyfikatów dla komputerów w domenie.  
  
## <a name="viewing-certificates"></a>Wyświetlanie certyfikatów  
 Do pracy z certyfikatami, często jest to konieczne je wyświetlić i sprawdzić ich właściwości. Łatwo to zrobić za pomocą narzędzia przystawkę Microsoft Management Console (MMC). Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie certyfikatów za pomocą przystawki programu MMC](how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Magazyny certyfikatów  
 Certyfikaty znajdują się w magazynach. Dwie lokalizacje magazynu głównych istnieją, które są podzielone na magazynach podrzędnych. Jeśli jesteś administratorem na komputerze, możesz wyświetlić obie magazynów głównych przy użyciu narzędzia przystawki programu MMC. Użytkownicy niebędący administratorami mogą wyświetlać tylko bieżącego magazynu użytkownika.  
  
- **Magazynu komputer lokalny**. Zawiera certyfikaty używane przez procesy maszyny, takich jak ASP.NET. Użyj tej lokalizacji można przechowywać certyfikaty uwierzytelniania serwera wobec klientów.  
  
- **Bieżący magazyn użytkownika**. Interaktywne aplikacje zwykle umieść tutaj certyfikaty dla bieżącego użytkownika komputera. Jeśli tworzysz aplikację kliencką, to zwykle umieszczane są certyfikaty, które przeprowadzają uwierzytelnianie użytkownika do usługi.  
  
 Te dwa magazyny są podzielone na magazynach podrzędnych. Najważniejsze z nich podczas programowania, korzystając z usługi WCF obejmują:  
  
- **Zaufane główne urzędy certyfikacji**. Certyfikaty można użyć w tym magazynie, aby utworzyć łańcuch certyfikatów, które można prześledzić do certyfikatu urzędu certyfikacji, w tym magazynie.  
  
    > [!IMPORTANT]
    >  Komputerze lokalnym domyślnie ufa wszystkich certyfikatów, umieszczane w tym magazynie nawet, jeśli certyfikat nie pochodzi z zaufanego firm urzędu certyfikacji. Z tego powodu nie należy umieszczać żadnych certyfikatów do tego magazynu chyba, że w pełni ufasz wystawcy i konsekwencje.  
  
- **Osobiste**. Ten magazyn jest używany dla certyfikatów skojarzonych z użytkownikiem komputerze. Zazwyczaj ten magazyn jest używany do certyfikatów wystawianych przez jeden z certyfikatów urzędów certyfikacji w magazynie zaufanych głównych urzędów certyfikacji. Alternatywnie tutaj certyfikat może być własnym wystawiony i zaufane przez aplikację.  
  
 Aby uzyskać więcej informacji na temat magazynów certyfikatów Zobacz [magazynów certyfikatów](/windows/desktop/secauthn/certificate-stores).  
  
### <a name="selecting-a-store"></a>Wybieranie Store  
 Wybieranie miejsce przechowywania certyfikatu zależy od sposobu i czasu uruchomienia usługi lub klienta. Obowiązują następujące reguły ogólne:  
  
- Jeśli usługa WCF jest hostowana w użyciu usługi Windows **komputera lokalnego** przechowywania. Należy pamiętać, że wymagane są uprawnienia administratora, aby zainstalować certyfikaty w magazynie komputera lokalnego.  
  
- Jeśli usługi lub klienta jest aplikacja, która jest uruchamiana na koncie użytkownika, użyj **bieżącego użytkownika** przechowywania.  
  
### <a name="accessing-stores"></a>Uzyskiwanie dostępu do magazynów  
 Magazyny są chronione przez listy kontroli dostępu (ACL), podobnie jak foldery na komputerze. Podczas tworzenia usługi hostowanej przez Internetowe usługi informacyjne (IIS), proces ASP.NET jest uruchamiany na koncie platformy ASP.NET. Konto musi mieć dostęp do magazynu który zawiera certyfikaty używane przez usługę. Każdy z magazynów głównych jest chroniony za pomocą domyślnej listy dostępu, ale listy mogą być modyfikowane. Jeśli utworzysz rolę oddzielne dostępu do magazynu, należy przyznać uprawnienia dostępu do tej roli. Aby dowiedzieć się, jak zmodyfikować listę dostępu za pomocą narzędzia WinHttpCertConfig.exe, zobacz [jak: Tworzenie certyfikatów tymczasowych do użycia podczas tworzenia](how-to-create-temporary-certificates-for-use-during-development.md). Aby uzyskać więcej informacji o korzystaniu z certyfikatów klienta z programem IIS, zobacz [sposób wywoływania usługi sieci Web przy użyciu certyfikatu klienta do uwierzytelniania w aplikacji internetowej ASP.NET](https://support.microsoft.com/en-us/help/901183/how-to-call-a-web-service-by-using-a-client-certificate-for-authentica).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Łańcuch zaufania i urzędy certyfikacji  
 Certyfikaty są tworzone w hierarchii, w którym każdego indywidualnego certyfikatu jest połączony z urzędem certyfikacji, który wystawił ten certyfikat. Jest to łącze do certyfikatu urzędu certyfikacji. Urząd certyfikacji certyfikatu następnie łączy się z urzędem certyfikacji, który wystawił certyfikat oryginalnego urzędu certyfikacji. Ten proces jest powtarzany, aż do osiągnięcia certyfikat głównego urzędu certyfikacji. Certyfikat głównego urzędu certyfikacji jest dodatkowo z natury zaufanych.  
  
 Certyfikaty cyfrowe są używane do uwierzytelniania jednostki, opierając się na tej hierarchii, nazywany również *łańcuch zaufania*. Możesz wyświetlić łańcuch dowolny certyfikat za pomocą przystawki programu MMC przez dwukrotne kliknięcie każdego certyfikatu, a następnie klikając **ścieżka certyfikatu** kartę. Aby uzyskać więcej informacji o importowaniu łańcuchów certyfikatów dla urzędu certyfikacji, zobacz [jak: Określanie łańcucha certyfikatu urzędu certyfikacji certyfikatu służącego do weryfikowania podpisów](specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Wszelkie wystawcy, może być wyznaczony zaufanego głównego urzędu certyfikacji, umieszczając wystawcy certyfikatu w magazynie certyfikatów zaufanego głównego urzędu.  
  
### <a name="disabling-chain-trust"></a>Wyłączanie łańcuch zaufania  
 Podczas tworzenia nowej usługi, używasz certyfikatu, który nie jest wystawiony przez zaufany certyfikat główny lub sam certyfikat wystawiającego certyfikaty mogą nie być w magazynie zaufanych głównych urzędów certyfikacji. Wyłącznie do celów programowania można tymczasowo wyłączyć mechanizm, który sprawdza, czy łańcuch zaufania certyfikatu. Aby to zrobić, należy ustawić `CertificateValidationMode` właściwości albo `PeerTrust` lub `PeerOrChainTrust`. Albo tryb oznacza, że certyfikat może albo własnym wystawiony (relacja zaufania elementów równorzędnych) lub jej część całego łańcucha zaufania. Właściwość można ustawić na żadnym z następujących klas.  
  
|Class|Właściwość|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Można również ustawić właściwości, za pomocą konfiguracji. Następujące elementy są używane do określania tryb weryfikacji:  
  
- [\<Uwierzytelnianie >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
- [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
- [\<messageSenderAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Uwierzytelnianie niestandardowe  
 `CertificateValidationMode` Właściwość umożliwia także dostosować sposób uwierzytelniania certyfikatów. Domyślnie ustawiono poziom `ChainTrust`. Aby użyć <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> wartości, należy także ustawić `CustomCertificateValidatorType` atrybutu do zestawu i typ używany do weryfikacji certyfikatu. Aby utworzyć niestandardowego modułu weryfikacji, musi dziedziczyć abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator> klasy.  
  
 Podczas tworzenia niestandardowego wystawcy uwierzytelnienia, jest najważniejszą metodą, aby zastąpić <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody. Na przykład niestandardowe uwierzytelnianie Zobacz [moduł weryfikacji certyfikatów X.509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) próbki. Aby uzyskać więcej informacji, zobacz [niestandardowe poświadczenia i Walidacja poświadczeń](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Za pomocą polecenia cmdlet programu PowerShell New-SelfSignedCertificate, aby zbudować łańcucha certyfikatów  
 Polecenia cmdlet programu PowerShell, New-SelfSignedCertificate tworzy certyfikaty X.509 i pary kluczy prywatnych klucza/publiczne. Można zapisać klucza prywatnego na dysku, a następnie użyć jej do wystawiania i Utwórz nowe certyfikaty, dlatego symulowania hierarchii certyfikatów połączonych. Polecenie cmdlet jest przeznaczona do użytku tylko jako pomoc podczas opracowywania usługi i nigdy nie powinien być używany do tworzenia certyfikatów, aby uzyskać rzeczywiste wdrożenie. Podczas tworzenia usługi WCF, wykonaj następujące kroki, aby utworzyć łańcuch zaufania za pomocą polecenia cmdlet New-SelfSignedCertificate.  
  
#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>Aby utworzyć łańcuch zaufania za pomocą polecenia cmdlet New-SelfSignedCertificate  
  
1. Tworzenie tymczasowego certyfikat głównego urzędu certyfikacji (podpisem) przy użyciu polecenia cmdlet New-SelfSignedCertificate. Zapisz klucz prywatny do dysku.  
  
2. Użyj nowego certyfikatu do wystawienia innego certyfikatu, który zawiera klucz publiczny.  
  
3. Zaimportuj certyfikat głównego urzędu certyfikacji do magazynu zaufanych głównych urzędów certyfikacji.  
  
4. Aby uzyskać instrukcje krok po kroku, zobacz [jak: Tworzenie certyfikatów tymczasowych do użycia podczas tworzenia](how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Który certyfikat do użycia?  
 Często zadawane pytania dotyczące certyfikatów są certyfikatu do użycia i dlaczego. Odpowiedź zależy od tego, czy programowania klienta lub usługę. Poniższe informacje zamieszczono ogólne wskazówki i nie jest wyczerpująca odpowiedzi na te pytania.  
  
### <a name="service-certificates"></a>Certyfikaty usługi  
 Certyfikaty usługi mają główne zadanie uwierzytelniania serwera wobec klientów. Jednym z sprawdzania początkowego, gdy klient uwierzytelnia serwer jest porównanie wartości **podmiotu** pole do jednolity identyfikator zasobów (URI) używane do kontaktu z usługą: DNS oba muszą być zgodne. Na przykład, jeśli identyfikator URI usługi jest `http://www.contoso.com/endpoint/` , a następnie **podmiotu** pole musi zawierać także wartość `www.contoso.com`.  
  
 Należy pamiętać, że pole może zawierać kilka wartości każdego prefiksem inicjowania, aby wskazać wartość. Najczęściej inicjowania jest "CN" dla nazwy pospolitej, na przykład `CN = www.contoso.com`. Istnieje również możliwość dla **podmiotu** pole to pole pozostanie puste, w którym to przypadku **alternatywna nazwa podmiotu** pole może zawierać **nazwy DNS** wartość.  
  
 Należy również zauważyć wartość **przeznaczone do celów** pole certyfikatu powinien zawierać odpowiednią wartość, takie jak "Uwierzytelnianie serwera" lub "Uwierzytelnienie klienta".  
  
### <a name="client-certificates"></a>Certyfikaty klienta  
 Certyfikaty klienta nie są zwykle wydawane przez urząd certyfikacji innych firm. Zamiast tego w bieżącej lokalizacji użytkownika w magazynie osobistym zazwyczaj zawiera certyfikaty, umieszczone tam przez urząd główny, z przeznaczeniem "Uwierzytelnienie klienta". Klient może używać takich certyfikatów, gdy jest wymagane uwierzytelnianie wzajemne.  
  
## <a name="online-revocation-and-offline-revocation"></a>Odwołań w trybie online i Offline odwołania  
  
### <a name="certificate-validity"></a>Ważność certyfikatu  
 Każdy certyfikat jest prawidłowy tylko dla danego okresu czasu, o nazwie *okres ważności*. Okres ważności jest definiowany przez **ważny od** i **ważny do** pola certyfikatu X.509. Podczas uwierzytelniania certyfikat jest sprawdzany w celu ustalenia, czy certyfikat jest nadal w okresie ważności.  
  
### <a name="certificate-revocation-list"></a>Lista odwołania certyfikatów  
 W dowolnym momencie podczas okresu ważności urzędu certyfikacji można odwołać się do certyfikatu. To może wystąpić wiele powodów, takich jak naruszenia bezpieczeństwa klucza prywatnego certyfikatu.  
  
 W takiej sytuacji sieciowych, co do których jest elementem podrzędnym elementu odwołanego certyfikatu są również nieprawidłowe i nie są zaufane podczas uwierzytelniania procedury. Aby dowiedzieć się o certyfikatach, które zostaną odwołane, a data sygnaturami czasowymi publikuje Każdy wystawca *listy odwołania certyfikatów* (CRL). Lista może zostać sprawdzone za pomocą odwołań w trybie online lub offline odwołania, ustawiając `RevocationMode` lub `DefaultRevocationMode` właściwość następujące klasy do jednego z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości wyliczenia: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> , a <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasy. Jest wartością domyślną dla wszystkich właściwości `Online`.  
  
 Można również ustawić tryb, w konfiguracji przy użyciu `revocationMode` zarówno atrybut [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) i [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (z [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>Metoda SetCertificate  
 W programie WCF często należy określić certyfikat lub zbiór certyfikaty usługi lub klient znajduje się na potrzeby uwierzytelniania, szyfrowania i cyfrowego podpisywania wiadomości. Można to zrobić programowo przy użyciu `SetCertificate` metoda różnych zajęciach, które reprezentują certyfikaty X.509. Następujące klasy użyj `SetCertificate` metodę, aby określić certyfikat.  
  
|Class|Metoda|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` Metoda działa poprzez podanie lokalizacji magazynu i Magazyn, typu "wyszukiwanie" (`x509FindType` parametru), który określa pole certyfikatu i wartość do znalezienia w polu. Na przykład, poniższy kod tworzy <xref:System.ServiceModel.ServiceHost> wystąpienia i ustawia certyfikat usługi, używany do uwierzytelniania usługi dla klientów z `SetCertificate` metody.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Wiele certyfikatów z taką samą wartość  
 Magazyn może zawierać wiele certyfikatów o takiej samej nazwie podmiotu. Oznacza to, że jeśli użytkownik określi, że `x509FindType` jest <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> lub <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>i więcej niż jeden certyfikat ma taką samą wartość, jest zgłaszany wyjątek, ponieważ nie istnieje sposób do odróżniania, który certyfikat jest wymagany. Można temu zaradzić, ustawiając `x509FindType` do <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Pole odcisk palca zawiera unikatową wartość, która może służyć do znalezienia określonego certyfikatu w magazynie. Jednak to ma swój własny wadą: Jeśli certyfikat jest odwołany lub odnowienia, `SetCertificate` metoda nie powiedzie się, ponieważ odcisk palca również został usunięty. Lub, jeśli certyfikat nie jest już prawidłowy, uwierzytelnianie nie powiedzie się. Sposób, aby rozwiązać ten problem, jest ustalenie `x590FindType` parametr <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> i określ nazwę wystawcy. Jeśli wymagana jest nie określonego wystawcę, można również ustawić jedną z innych <xref:System.Security.Cryptography.X509Certificates.X509FindType> wartości wyliczenia, takich jak <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Certyfikaty w konfiguracji  
 Certyfikaty można również ustawić za pomocą konfiguracji. Jeśli tworzysz usługę poświadczeń, takich jak certyfikaty, są określone w obszarze [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Podczas programowania klienta certyfikaty są określone w obszarze [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Mapowanie certyfikatu do konta użytkownika  
 Funkcja usług IIS i usługi Active Directory jest zdolność do mapowania certyfikatu na konto użytkownika Windows. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [mapowania certyfikatów do kont użytkowników](https://go.microsoft.com/fwlink/?LinkId=88917).  
  
 Aby uzyskać więcej informacji o używaniu mapowanie usługi Active Directory, zobacz [mapowania certyfikatów klientów przy użyciu mapowanie usługi katalogowej](https://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Dzięki tej możliwości jest włączone, można ustawić <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> właściwość <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> klasy `true`. W konfiguracji, można ustawić `mapClientCertificateToWindowsAccount` atrybutu [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) elementu `true`, jak pokazano w poniższym kodzie.  
  
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
  
 Mapowania certyfikatu X.509 do tokenu, który reprezentuje konto użytkownika Windows uznaje podniesienie uprawnień, ponieważ po mapowane, tokenu Windows można użyć do uzyskania dostępu do chronionych zasobów. W związku z tym zasady domeny wymaga certyfikatu X.509, zachowanie zgodności z zasadami, jego przed mapowania. *SChannel* pakiet zabezpieczeń wymusza to wymaganie.  
  
 Korzystając z [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszej, WCF zapewnia certyfikat jest zgodny z zasad domeny, zanim jest mapowany do konta Windows.  
  
 W pierwszej wersji programu WCF mapowanie odbywa się bez konsultacji zasady domeny. W związku z tym jest możliwe, że starsze aplikacje, które dawniej pracowałam podczas uruchamiania w pierwszej wersji zakończy się niepowodzeniem, jeśli mapowanie jest włączona, a certyfikat X.509 nie spełnia warunków zasady domeny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Security>
- <xref:System.ServiceModel>
- <xref:System.Security.Cryptography.X509Certificates.X509FindType>
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
