---
title: Praca z certyfikatami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: e38ead0d378092af086218277fd2e85b4a6396c3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746889"
---
# <a name="working-with-certificates"></a>Praca z certyfikatami

W przypadku zabezpieczeń programu Windows Communication Foundation (WCF), certyfikaty cyfrowe X. 509 są często używane do uwierzytelniania klientów i serwerów, szyfrowania i cyfrowego podpisywania wiadomości. W tym temacie krótko opisano funkcje certyfikatu cyfrowego X. 509 oraz sposób ich używania w programie WCF oraz linki do tematów, które wyjaśniają te koncepcje w dalszej części lub pokazują, jak wykonywać typowe zadania przy użyciu usług WCF i certyfikatów.

W skrócie certyfikat cyfrowy jest częścią *infrastruktury kluczy publicznych* (PKI), która jest systemem certyfikatów cyfrowych, urzędów certyfikacji i innych urzędów rejestrowania, którzy weryfikują i uwierzytelniają okres ważności każdej ze stron w ramach transakcji elektronicznej przy użyciu kryptografii klucza publicznego. Urząd certyfikacji wystawia certyfikaty, a każdy certyfikat zawiera zestaw pól zawierających dane, takich jak *podmiot* (podmiot, dla którego wystawiony jest certyfikat), daty ważności (gdy certyfikat jest ważny), wystawca (jednostka, która wystawił certyfikat) i klucz publiczny. W programie WCF każda z tych właściwości jest przetwarzana jako <xref:System.IdentityModel.Claims.Claim>, a każde z nich jest dalej podzielone na dwa typy: tożsamość i prawo. Aby uzyskać więcej informacji na temat certyfikatów X. 509, zobacz [Certyfikaty klucza publicznego x. 509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Aby uzyskać więcej informacji o oświadczeniach i autoryzacji w programie WCF, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](managing-claims-and-authorization-with-the-identity-model.md). Aby uzyskać więcej informacji o implementowaniu infrastruktury kluczy publicznych, zobacz [infrastruktura PKI przedsiębiorstwa z systemem Windows Server 2012 R2 Active Directory usług certyfikatów](https://docs.microsoft.com/archive/blogs/yungchou/enterprise-pki-with-windows-server-2012-r2-active-directory-certificate-services-part-1-of-2).

Podstawową funkcją certyfikatu jest uwierzytelnianie tożsamości właściciela certyfikatu dla innych osób. Certyfikat zawiera *klucz publiczny* właściciela, podczas gdy właściciel zachowuje klucz prywatny. Klucz publiczny może służyć do szyfrowania wiadomości wysyłanych do właściciela certyfikatu. Tylko właściciel ma dostęp do klucza prywatnego, więc tylko właściciel może odszyfrować te komunikaty.

Certyfikaty muszą być wystawiane przez urząd certyfikacji, który jest często wystawcą certyfikatów innych firm. W domenie systemu Windows jest uwzględniany urząd certyfikacji, którego można użyć do wystawiania certyfikatów dla komputerów w domenie.

## <a name="viewing-certificates"></a>Wyświetlanie certyfikatów

Aby można było korzystać z certyfikatów, często konieczne jest ich wyświetlenie i sprawdzenie ich właściwości. Można to łatwo zrobić przy użyciu przystawki programu Microsoft Management Console (MMC). Aby uzyskać więcej informacji, zobacz [How to: View Certificates za pomocą przystawki MMC](how-to-view-certificates-with-the-mmc-snap-in.md).

## <a name="certificate-stores"></a>Magazyny certyfikatów

Certyfikaty znajdują się w sklepach. Istnieją dwa główne lokalizacje magazynu, które są dalej podzielone na magazyny podrzędne. Jeśli jesteś administratorem na komputerze, możesz wyświetlić oba magazyny główne przy użyciu narzędzia MMC przystawka. Użytkownicy niebędący administratorami mogą wyświetlać tylko bieżący magazyn użytkowników.

- **Magazyn komputera lokalnego**. Zawiera certyfikaty, do których uzyskuje dostęp procesy maszyny, takie jak ASP.NET. Ta lokalizacja służy do przechowywania certyfikatów uwierzytelniających serwer na klientach programu.

- **Bieżący magazyn użytkownika**. Aplikacje interaktywne zwykle umieszczają tutaj certyfikaty dla bieżącego użytkownika komputera. W przypadku tworzenia aplikacji klienckiej zwykle umieszczane są certyfikaty uwierzytelniające użytkownika w usłudze.

Te dwa magazyny są dalej podzielone na magazyny podrzędne. Najważniejszymi z nich podczas programowania przy użyciu programu WCF są:

- **Zaufane główne urzędy certyfikacji**. Możesz użyć certyfikatów w tym magazynie do utworzenia łańcucha certyfikatów, które można wyśledzić z powrotem do certyfikatu urzędu certyfikacji w tym magazynie.

  > [!IMPORTANT]
  > Komputer lokalny niejawnie ufa wszystkie certyfikaty znajdujące się w tym magazynie, nawet jeśli certyfikat nie pochodzi od zaufanego urzędu certyfikacji innej firmy. Z tego powodu nie należy umieszczać żadnych certyfikatów w tym magazynie, chyba że w pełni ufasz wystawcy i nie zrozumiesz konsekwencji.

- **Osobiste**. Ten magazyn jest używany w przypadku certyfikatów skojarzonych z użytkownikiem komputera. Zazwyczaj ten magazyn jest używany w przypadku certyfikatów wystawionych przez jeden z certyfikatów urzędu certyfikacji znajdujących się w magazynie zaufanych głównych urzędów certyfikacji. Certyfikat odnaleziony w tym miejscu może być również wystawiony i zaufany przez aplikację.

Aby uzyskać więcej informacji na temat magazynów certyfikatów, zobacz [magazyny certyfikatów](/windows/desktop/secauthn/certificate-stores).

### <a name="selecting-a-store"></a>Wybieranie magazynu

Wybór lokalizacji przechowywania certyfikatu zależy od tego, jak i kiedy uruchomiona jest usługa lub klient. Obowiązują następujące reguły ogólne:

- Jeśli usługa WCF jest hostowana w usłudze systemu Windows, użyj **lokalnego magazynu maszynowego** . Należy pamiętać, że uprawnienia administratora są wymagane do zainstalowania certyfikatów w magazynie komputera lokalnego.

- Jeśli usługa lub klient jest aplikacją, która jest uruchamiana na koncie użytkownika, Użyj bieżącego magazynu **użytkownika** .

### <a name="accessing-stores"></a>Uzyskiwanie dostępu do sklepów

Magazyny są chronione przez listy kontroli dostępu (ACL), podobnie jak foldery na komputerze. Podczas tworzenia usługi hostowanej przez Internet Information Services (IIS) proces ASP.NET jest uruchamiany w ramach konta ASP.NET. To konto musi mieć dostęp do magazynu zawierającego certyfikaty używane przez usługę. Każdy z głównych magazynów jest chroniony przy użyciu domyślnej listy dostępu, ale listy można modyfikować. Jeśli utworzysz osobną rolę w celu uzyskania dostępu do magazynu, musisz udzielić uprawnienia dostępu do tej roli. Aby dowiedzieć się, jak zmodyfikować listę dostępu za pomocą narzędzia WinHttpCertConfig. exe, zobacz [How to: Create Temporary Certificates for use in Development](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="chain-trust-and-certificate-authorities"></a>Zaufanie łańcuchowe i urzędy certyfikacji

Certyfikaty są tworzone w hierarchii, w której każdy pojedynczy certyfikat jest połączony z urzędem certyfikacji, który wystawił certyfikat. Ten link jest certyfikatem urzędu certyfikacji. Następnie certyfikat urzędu certyfikacji łączy się z urzędem certyfikacji, który wystawił certyfikat oryginalnego urzędu certyfikacji. Ten proces jest powtarzany do momentu osiągnięcia certyfikatu głównego urzędu certyfikacji. Certyfikat głównego urzędu certyfikacji jest zaufany.

Certyfikaty cyfrowe są używane do uwierzytelniania jednostki przy użyciu tej hierarchii, nazywanej również *łańcuchem zaufania*. Aby wyświetlić łańcuch certyfikatów za pomocą przystawki programu MMC, kliknij dwukrotnie dowolny certyfikat, a następnie kliknij kartę **ścieżka certyfikatu** . Aby uzyskać więcej informacji na temat importowania łańcuchów certyfikatów dla urzędu certyfikacji, zobacz [How to: Określanie łańcucha certyfikatu urzędu certyfikacji służącego do weryfikowania podpisów](specify-the-certificate-authority-chain-verify-signatures-wcf.md).

> [!NOTE]
> Każdy wystawca może zostać wyznaczyć zaufany urząd główny przez umieszczenie certyfikatu wystawcy w magazynie certyfikatów zaufanego urzędu głównego.

### <a name="disabling-chain-trust"></a>Wyłączanie zaufania łańcucha

Podczas tworzenia nowej usługi może być używany certyfikat, który nie jest wystawiony przez zaufany certyfikat główny, lub sam certyfikat wystawiający może nie znajdować się w magazynie zaufanych głównych urzędów certyfikacji. Tylko do celów programistycznych można tymczasowo wyłączyć mechanizm, który sprawdza łańcuch zaufania dla certyfikatu. W tym celu należy ustawić właściwość `CertificateValidationMode` na `PeerTrust` lub `PeerOrChainTrust`. Każdy tryb określa, że certyfikat może być wystawiony samodzielnie (relacja równorzędna) lub część łańcucha zaufania. Właściwość można ustawić dla dowolnej z następujących klas.

|Class|Właściwość|
|-----------|--------------|
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|

Możesz również ustawić właściwość za pomocą konfiguracji. Następujące elementy są używane do określania trybu walidacji:

- [> uwierzytelniania \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)

- [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)

- [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)

## <a name="custom-authentication"></a>Uwierzytelnianie niestandardowe

Właściwość `CertificateValidationMode` umożliwia również dostosowanie sposobu uwierzytelniania certyfikatów. Domyślnie poziom jest ustawiony na `ChainTrust`. Aby użyć wartości <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>, należy również ustawić atrybut `CustomCertificateValidatorType` na zestaw i typ używany do walidacji certyfikatu. Aby utworzyć niestandardowy moduł sprawdzania poprawności, należy dziedziczyć z klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator>.

Podczas tworzenia niestandardowego wystawcy, najważniejszym sposobem przesłonięcia jest metoda <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A>. Aby zapoznać się z przykładem uwierzytelniania niestandardowego, zobacz przykład [modułu sprawdzania poprawności certyfikatu X. 509](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) . Aby uzyskać więcej informacji, zobacz [Niestandardowe poświadczenia i sprawdzanie poprawności poświadczeń](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).

## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Tworzenie łańcucha certyfikatów przy użyciu polecenia cmdlet New-SelfSignedCertificate programu PowerShell

Polecenie cmdlet New-SelfSignedCertificate programu PowerShell tworzy certyfikaty X. 509 oraz pary kluczy prywatnych/kluczy publicznych. Możesz zapisać klucz prywatny na dysku, a następnie użyć go do wystawienia i podpisania nowych certyfikatów, co symuluje hierarchię certyfikatów łańcucha. Polecenie cmdlet jest przeznaczone do użycia tylko jako pomoc podczas tworzenia usług i nigdy nie powinno być używane do tworzenia certyfikatów do rzeczywistego wdrożenia. Podczas tworzenia usługi WCF wykonaj następujące kroki, aby utworzyć łańcuch zaufania za pomocą polecenia cmdlet New-SelfSignedCertificate.

#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>Aby utworzyć łańcuch zaufania za pomocą polecenia cmdlet New-SelfSignedCertificate

1. Utwórz tymczasowy certyfikat głównego urzędu certyfikacji za pomocą polecenia cmdlet New-SelfSignedCertificate. Zapisz klucz prywatny na dysku.

2. Użyj nowego certyfikatu w celu wystawienia innego certyfikatu zawierającego klucz publiczny.

3. Zaimportuj certyfikat głównego urzędu do magazynu zaufanych głównych urzędów certyfikacji.

4. Aby uzyskać instrukcje krok po kroku, zobacz [How to: Create Temporary Certificates for use in Development](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="which-certificate-to-use"></a>Którego certyfikatu użyć?

Często zadawane pytania dotyczące certyfikatów to certyfikat, który ma być używany, i dlaczego. Odpowiedź zależy od tego, czy program ma być programowaniem klienta czy usługi. Poniższe informacje stanowią ogólne wytyczne i nie stanowią wyczerpującej odpowiedzi na te pytania.

### <a name="service-certificates"></a>Certyfikaty usługi

Certyfikaty usługi mają podstawowe zadanie uwierzytelniania serwera na klientach programu. Jednym z początkowych testów, gdy klient uwierzytelnia serwer, to porównanie wartości pola **podmiotu** z Uniform Resource Identifier (URI) użytego do skontaktowania się z usługą: serwer DNS obu musi być zgodny. Na przykład jeśli identyfikator URI usługi jest `http://www.contoso.com/endpoint/`, pole **podmiotu** również musi zawierać wartość `www.contoso.com`.

Należy zauważyć, że pole może zawierać kilka wartości, z których każda poprzedza inicjalizację, aby wskazać wartość. Najczęściej Inicjalizacja jest "CN" dla nazwy pospolitej, na przykład `CN = www.contoso.com`. Możliwe jest również, aby pole **subject** było puste. w takim przypadku pole **Nazwa alternatywna podmiotu** może zawierać wartość **nazwy DNS** .

Należy również zwrócić uwagę, że wartość pola **zamierzone cele** certyfikatu powinna zawierać odpowiednią wartość, na przykład "uwierzytelnianie serwera" lub "Uwierzytelnianie klienta".

### <a name="client-certificates"></a>Certyfikaty klienta

Certyfikaty klienta nie są zwykle wydawane przez urząd certyfikacji innej firmy. Zamiast tego magazyn osobisty bieżącej lokalizacji użytkownika zwykle zawiera certyfikaty znajdujące się w urzędzie głównym z zamierzonym celem "Uwierzytelnianie klienta". Klient może użyć takiego certyfikatu, gdy wymagane jest wzajemne uwierzytelnianie.

## <a name="online-revocation-and-offline-revocation"></a>Odwoływanie do trybu online i odwoływanie do trybu offline

### <a name="certificate-validity"></a>Ważność certyfikatu

Każdy certyfikat jest ważny tylko przez dany okres czasu, nazywany *okresem ważności*. Okres ważności jest definiowany przez prawidłowe wartości pól **od** i **ważny do** dla certyfikatu X. 509. Podczas uwierzytelniania certyfikat jest sprawdzany w celu ustalenia, czy certyfikat jest nadal w okresie ważności.

### <a name="certificate-revocation-list"></a>Lista odwołania certyfikatów

W dowolnym momencie w okresie ważności urząd certyfikacji może odwołać certyfikat. Może się to zdarzyć z wielu powodów, takich jak naruszenie klucza prywatnego certyfikatu.

W takim przypadku wszystkie łańcuchy, które są podrzędne od odwołanego certyfikatu, są również nieprawidłowe i nie są zaufane podczas procedur uwierzytelniania. Aby dowiedzieć się, które certyfikaty zostały odwołane, Każdy wystawca publikuje *listę odwołania certyfikatów* (CRL) z sygnaturą czasową i datą. Listę można sprawdzić za pomocą odwołania online lub odwoływania do trybu offline przez ustawienie właściwości `RevocationMode` lub `DefaultRevocationMode` następujących klas na jedną z <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> wartości wyliczenia: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>i <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klas. Wartość domyślna dla wszystkich właściwości jest `Online`.

Można również ustawić tryb konfiguracji przy użyciu `revocationMode` atrybutu [\<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) ( [\<usługi servicebehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) i [\<authentication](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) > (\<[endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).

## <a name="the-setcertificate-method"></a>Metoda SetCertificate

W programie WCF należy często określić certyfikat lub zestaw certyfikatów, których usługa lub klient ma używać do uwierzytelniania, szyfrowania lub cyfrowego podpisywania wiadomości. Można to zrobić programowo przy użyciu metody `SetCertificate` różnych klas, które reprezentują certyfikaty X. 509. Poniższe klasy wykorzystują metodę `SetCertificate`, aby określić certyfikat.

|Class|Metoda|
|-----------|------------|
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|

Metoda `SetCertificate` działa przez wyznaczanie lokalizacji i magazynu magazynu, typu "Find" (`x509FindType` parametru), który określa pole certyfikatu oraz wartość do znalezienia w polu. Na przykład poniższy kod tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> i ustawia certyfikat usługi używany do uwierzytelniania usługi na klientach przy użyciu metody `SetCertificate`.

[!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
[!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]

### <a name="multiple-certificates-with-the-same-value"></a>Wiele certyfikatów o tej samej wartości

Magazyn może zawierać wiele certyfikatów o tej samej nazwie podmiotu. Oznacza to, że w przypadku określenia, że `x509FindType` jest <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> lub <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>i więcej niż jeden certyfikat ma taką samą wartość, wyjątek jest zgłaszany, ponieważ nie ma możliwości odróżnienia certyfikatu, który jest wymagany. Można to ograniczyć przez ustawienie `x509FindType`, aby <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Pole odcisk palca zawiera unikatową wartość, która może być używana do znajdowania określonego certyfikatu w magazynie. Jest to jednak własne niekorzystne: Jeśli certyfikat zostanie odwołany lub odnowiony, Metoda `SetCertificate` nie powiedzie się, ponieważ odcisk palca również został usunięty. Lub jeśli certyfikat nie jest już ważny, uwierzytelnianie kończy się niepowodzeniem. Sposobem na ograniczenie tego problemu jest ustawienie `x590FindType` parametru <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> i określenie nazwy wystawcy. Jeśli określony wystawca nie jest wymagany, można również ustawić jedną z innych <xref:System.Security.Cryptography.X509Certificates.X509FindType> wartości wyliczenia, takich jak <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.

## <a name="certificates-in-configuration"></a>Certyfikaty w konfiguracji

Można również ustawić certyfikaty przy użyciu opcji konfiguracja. Jeśli tworzysz usługę, poświadczenia, w tym certyfikaty, są określone w [>\<serviceBehaviors](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Podczas programowania klienta certyfikaty są określane w [\<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).

## <a name="mapping-a-certificate-to-a-user-account"></a>Mapowanie certyfikatu na konto użytkownika

Funkcją usług IIS i Active Directory jest możliwość mapowania certyfikatu na konto użytkownika systemu Windows. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Mapowanie certyfikatów na konta użytkowników](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc736706(v=ws.10)).

Aby uzyskać więcej informacji o korzystaniu z mapowania Active Directory, zobacz [Mapowanie certyfikatów klienta przy użyciu mapowania usługi katalogowej](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc758484(v=ws.10)).

Korzystając z tej możliwości, można ustawić właściwość <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> klasy <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> na `true`. W obszarze Konfiguracja można ustawić atrybut `mapClientCertificateToWindowsAccount` elementu [\<authentication >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) na `true`, jak pokazano w poniższym kodzie.

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

Mapowanie certyfikatu X. 509 na token reprezentujący konto użytkownika systemu Windows jest uznawane za podniesienie uprawnień, ponieważ po zmapowaniu token systemu Windows może służyć do uzyskania dostępu do chronionych zasobów. Dlatego zasady domeny wymagają, aby certyfikat X. 509 był zgodny z zasadami przed mapowaniem. Pakiet zabezpieczeń *Schannel* wymusza to wymaganie.

W przypadku korzystania z .NET Framework 3,5 lub nowszych wersji usługa WCF gwarantuje, że certyfikat jest zgodny z zasadami domeny, zanim zostanie zmapowany na konto systemu Windows.

W pierwszej wersji programu WCF mapowanie jest wykonywane bez konsultacji z zasadami domeny. W związku z tym jest możliwe, że starsze aplikacje, które były używane podczas uruchamiania w pierwszej wersji, zakończą się niepowodzeniem, jeśli mapowanie jest włączone i certyfikat X. 509 nie spełnia zasad domeny.

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Security>
- <xref:System.ServiceModel>
- <xref:System.Security.Cryptography.X509Certificates.X509FindType>
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
