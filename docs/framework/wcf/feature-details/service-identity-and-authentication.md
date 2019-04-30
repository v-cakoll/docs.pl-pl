---
title: Uwierzytelnianie i tożsamość usług
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [WCF], specifying the identity of a service
ms.assetid: a4c8f52c-5b30-45c4-a545-63244aba82be
ms.openlocfilehash: f33144c320b3648f9e201505a34ed8f1ecd5965b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61748268"
---
# <a name="service-identity-and-authentication"></a>Uwierzytelnianie i tożsamość usług
Usługa *tożsamość punktu końcowego* jest wartością wygenerowany na podstawie usługi sieci Web Services Description Language (WSDL). Ta wartość propagowane do dowolnego klienta jest używany do uwierzytelniania usługi. Po klient inicjuje komunikację do punktu końcowego i usługa uwierzytelnia klienta, klient porównuje wartości tożsamości punktu końcowego z procesu uwierzytelniania punktu końcowego, zwrócona wartość. Jeśli są zgodne, klient jest pewność, że skontaktuje się z punktem końcowym usługi oczekiwane. Ta opcja działa jako ochrony przed *wyłudzania informacji* poprzez uniemożliwienie nastąpi przekierowanie do punktu końcowego hostowanego przez usługę złośliwego klienta.  
  
 Aby uzyskać przykładową aplikację prezentującą ustawienie tożsamości, zobacz [tożsamość usług — przykład](../../../../docs/framework/wcf/samples/service-identity-sample.md). Aby uzyskać więcej informacji na temat punktów końcowych oraz adresy punktów końcowych, zobacz [adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md).  
  
> [!NOTE]
>  Jeśli LanMan NT (NTLM) jest używany do uwierzytelniania, tożsamość usługi nie jest zaznaczone, ponieważ w ramach uwierzytelniania NTLM, klient będzie mógł uwierzytelniania serwera. Uwierzytelnianie NTLM jest używany, gdy komputer jest częścią grupy roboczej Windows lub w przypadku, gdy uruchomiona starsza wersja systemu Windows, który nie obsługuje uwierzytelniania Kerberos.  
  
 Podczas inicjowania przez klienta bezpiecznego kanału do wysyłania komunikatu do usługi nad nią uwierzytelnia usługi infrastruktury usług Windows Communication Foundation (WCF) i tylko, jeśli tożsamość usługi jest zgodne z tożsamością, określona w punkcie końcowym, wysyła komunikat adres klienta używa.  
  
 Przetwarzanie tożsamości składa się z następujących etapów:  
  
- W czasie projektowania dewelopera klienta określa tożsamość usługi z punktu końcowego metadanych (dostępna za pośrednictwem WSDL).  
  
- W czasie wykonywania aplikacja klienta sprawdza oświadczenia poświadczenia zabezpieczeń, przed wysłaniem komunikatów do usługi.  
  
 Tożsamość przetwarzania na kliencie jest analogiczne do uwierzytelniania klienta w usłudze. Usługa bezpiecznego nie wykonuje kodu, dopóki nie zostały uwierzytelnione poświadczenia klienta. Podobnie klient nie wysyła komunikaty do usługi, dopóki nie zostały uwierzytelnione poświadczenia zależy od tego, co jest znane z wyprzedzeniem z metadanych usługi.  
  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość <xref:System.ServiceModel.EndpointAddress> klasa reprezentuje tożsamość usługi o nazwie przez klienta. Usługi <xref:System.ServiceModel.EndpointAddress.Identity%2A> w metadanych. Po uruchomieniu dewelopera klienta [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) względem punktu końcowego usługi wygenerowaną konfigurację zawiera wartość usługi <xref:System.ServiceModel.EndpointAddress.Identity%2A> właściwości. Infrastruktura WCF (jeśli jest skonfigurowane z zabezpieczeniami) sprawdza, czy usługa posiada określono tożsamości.  
  
> [!IMPORTANT]
>  Metadane zawiera oczekiwaną tożsamość usługi, dlatego zalecane jest, udostępnianie metadanych usługi w bezpieczny sposób, na przykład przez utworzenie punktu końcowego HTTPS dla usługi. Aby uzyskać więcej informacji, zobacz [jak: Bezpieczne punkty końcowe metadanych](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
## <a name="identity-types"></a>Typów tożsamości  
 Usługa może zapewnić sześć typów tożsamości. Każdy typ tożsamości odnosi się do elementu, który można umieścić wewnątrz `<identity>` element w konfiguracji. Typ używany jest zależny od scenariusza i wymagań dotyczących zabezpieczeń usługi. W poniższej tabeli opisano każdy typ tożsamości.  
  
|Typ tożsamości|Opis|Typowy scenariusz|  
|-------------------|-----------------|----------------------|  
|System nazw domen (DNS)|Użyj tego elementu za pomocą certyfikatów X.509 lub konta Windows. Porównuje nazwę DNS określony w poświadczeniu za pomocą wartości określonej w tym elemencie.|Sprawdzanie DNS umożliwia używanie certyfikatów z usługą DNS lub nazwy podmiotu. Jeśli certyfikat jest utworzony ponownie z tej samej DNS lub nazwy podmiotu, sprawdzić tożsamości jest nadal ważny. Gdy certyfikat jest ponownie, pobiera nowego klucza RSA, ale zachowuje DNS tego samego lub nazwy podmiotu. Oznacza to, że klienci nie muszą zaktualizować swoje informacje identyfikacyjne dotyczące usługi.|  
|certyfikat. Domyślnie gdy `ClientCredentialType` jest ustawiona na certyfikacie.|Ten element określa wartość certyfikat X.509 szyfrowany algorytmem Base64 do porównania z klienta.<br /><br /> Ten element służy również, korzystając z [!INCLUDE[infocard](../../../../includes/infocard-md.md)] jako poświadczeń do uwierzytelniania usługi.|Ten element ogranicza uwierzytelniania do pojedynczego certyfikatu na podstawie jego wartość odcisku palca. Umożliwia użycie uwierzytelniania bardziej rygorystyczne, ponieważ wartości odcisku palca są unikatowe. Obejmuje to jedno zastrzeżenie:: Jeśli certyfikat jest utworzony ponownie z taką samą nazwę podmiotu, ma również nowy odcisk palca. W związku z tym klienci nie będą mogli zweryfikować usługi, chyba że nowy odcisk palca jest znany. Aby uzyskać więcej informacji na temat znajdowania odcisk palca certyfikatu, zobacz [jak: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).|  
|Odwołanie certyfikatu|Taka sama jak opcja certyfikat opisanych powyżej. Jednak ten element umożliwia Określ nazwę certyfikatu i lokalizacji, z którego można pobrać certyfikat magazynu.|Wartość taka sama jak w scenariuszu certyfikatu z opisem w poprzedniej sekcji.<br /><br /> Korzyścią jest to, że można zmienić lokalizację magazynu certyfikatów.|  
|RSA|Ten element określa wartość klucza RSA do porównania z klienta. Jest to podobne do opcji/certyfikatu, ale zamiast używania odcisk palca certyfikatu, klucza RSA certyfikatu jest używana w zamian.|Sprawdzanie RSA umożliwia takie ograniczenie uwierzytelniania do pojedynczego certyfikatu na podstawie jego klucza RSA. Umożliwia to bardziej rygorystyczne uwierzytelniania określonego klucza RSA kosztem usługi, która nie jest już współpracuje z istniejącymi klientami, gdy zmieni się wartość klucza RSA.|  
|Główna nazwa użytkownika (UPN). Domyślnie podczas `ClientCredentialType` ustawiono Windows i usługą proces nie jest uruchomiony w ramach jednego konta system.|Ten element Określa nazwę UPN, która jest uruchomiona w obszarze. W sekcji protokołu Kerberos i tożsamości [przesłanianie tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Daje to gwarancję, że usługa jest uruchomiona w ramach określonego konta użytkownika Windows. Konto użytkownika może być bieżący użytkownik zalogowany lub usługa uruchomiona w ramach określonego konta użytkownika.<br /><br /> To ustawienie korzysta ze zabezpieczeń Windows Kerberos, jeśli usługa jest uruchomiona w ramach konta domeny w środowisku usługi Active Directory.|  
|Główna nazwa usługi (SPN). Domyślnie gdy `ClientCredentialType` ustawiono Windows i usługą proces jest uruchomiony w ramach jednego z kont systemu — Usługa lokalna, LocalSystem lub NetworkService.|Ten element Określa nazwę SPN, skojarzone z kontem usługi. W sekcji protokołu Kerberos i tożsamości [przesłanianie tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).|Daje to gwarancję, że nazwy SPN i określonego konta Windows skojarzone z nazwy SPN identyfikowania usługi.<br /><br /> Aby skojarzyć konto komputera dla konta użytkownika usługi, można użyć narzędzia Setspn.exe.<br /><br /> To ustawienie korzysta z Windows Kerberos, zabezpieczenia, jeśli usługa jest uruchomiona w ramach jednego z kont systemowych, lub w ramach konta domeny, który ma nazwę SPN skojarzone z jego oraz komputerem domeny w środowisku usługi Active Directory.|  
  
## <a name="specifying-identity-at-the-service"></a>Określanie tożsamości na usługę  
 Zazwyczaj nie trzeba ustawić tożsamość usługi, ponieważ wybór typu poświadczeń klienta decyduje o rodzaju tożsamości widoczne w metadanych usługi. Aby uzyskać więcej informacji o tym, jak zastąpić, lub określić tożsamość usługi, zobacz [przesłanianie tożsamości usługi na potrzeby uwierzytelniania](../../../../docs/framework/wcf/extending/overriding-the-identity-of-a-service-for-authentication.md).  
  
## <a name="using-the-identity-element-in-configuration"></a>Za pomocą \<tożsamości > Element w konfiguracji  
 Jeśli zmienisz typ poświadczeń klienta w powiązaniu z wcześniejszymi do `Certificate,` wygenerowanego pliku WSDL zawiera Base64 z serializacji, a następnie certyfikat X.509 dla wartości tożsamości, jak pokazano w poniższym kodzie. Jest to wartość domyślna dla wszystkich typów poświadczeń klienta inne niż Windows.  

 Można zmienić wartości domyślnej tożsamości usługi lub zmienić typ tożsamości za pomocą `<identity>` element konfiguracji lub przez ustawienie tożsamości w kodzie. Poniższy kod konfiguracji ustawia tożsamość system (DNS) nazwę domeny, z wartością `contoso.com`.  

## <a name="setting-identity-programmatically"></a>Programowe Ustawianie tożsamości  
 Usługa nie ma jawnie określić tożsamości, ponieważ automatycznie określa WCF. Jednak WCF można określić tożsamość w punkcie końcowym, jeśli jest to wymagane. Poniższy kod dodaje nowy punkt końcowy usługi w kontekście określonej tożsamości DNS.  
  
 [!code-csharp[C_Identity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#5)]
 [!code-vb[C_Identity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#5)]  
  
## <a name="specifying-identity-at-the-client"></a>Określanie tożsamości klienta  
 W czasie projektowania, zazwyczaj używa dewelopera klienta [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do wygenerowania konfiguracji klienta. Wygenerowano plik konfiguracyjny (przeznaczone do użytku przez klienta) zawiera tożsamości serwera. Na przykład poniższy kod jest generowany z usługi, która określa tożsamość DNS, jak pokazano w powyższym przykładzie. Należy zauważyć, że wartość tożsamości punktu końcowego klienta jest zgodny z typem usługi. W tym przypadku, gdy klient odbierze poświadczenia Windows (Kerberos) dla usługi, oczekuje, że wartość `contoso.com`.  

 Jeśli zamiast Windows, usługa Określa certyfikat jako typu poświadczeń klienta, a następnie właściwość DNS certyfikatu powinien być wartością `contoso.com`. (Lub, jeśli właściwość DNS jest `null`, nazwa podmiotu certyfikatu musi być `contoso.com`.)  
  
#### <a name="using-a-specific-value-for-identity"></a>Przy użyciu określonej wartości tożsamości  
 Następujący plik konfiguracji klienta pokazuje, jak powinna być określona wartość tożsamości usługi. W poniższym przykładzie klient może komunikować się z dwoma punktami końcowymi. Pierwszy jest identyfikowany za pomocą odcisku palca certyfikatu, a druga za pomocą klucza RSA certyfikatu. Oznacza to, że certyfikat, który zawiera tylko publiczny klucz/prywatnego pary kluczy, ale nie jest wystawiony przez zaufany urząd.  

## <a name="identity-checking-at-run-time"></a>Tożsamość sprawdzanie w czasie wykonywania  
 W czasie projektowania dewelopera klienta określa tożsamość serwera za pośrednictwem jego metadanych. W czasie wykonywania sprawdzanie tożsamości jest wykonywane przed wywołaniem żadnych punktów końcowych usługi.  
  
 Wartość tożsamości jest powiązany typ uwierzytelniania, określony przez metadane innymi słowy typ poświadczenia używane przez usługę.  
  
 Jeśli kanał jest skonfigurowany do uwierzytelniania za pomocą komunikatów lub poziomie transportu Secure Sockets Layer (SSL) za pomocą certyfikatów X.509 do uwierzytelniania, następujące wartości tożsamości są prawidłowe:  
  
- DNS. WCF zapewnia, że certyfikat oferowane w trakcie uzgadniania protokołu SSL zawiera DNS lub `CommonName` atrybutu (CN) jest równa wartości określonej w tożsamość DNS na komputerze klienckim. Należy pamiętać, że te testy są wykonywane tylko dodatkowo do określenia ważności certyfikatu serwera. Domyślnie WCF weryfikuje, czy certyfikat serwera jest wystawiony przez zaufanego głównego urzędu certyfikacji.  
  
- certyfikat. Podczas uzgadniania protokołu SSL WCF gwarantuje, że zdalnego punktu końcowego udostępnia wartość dokładnie certyfikat określony w tożsamości.  
  
- Odwołanie certyfikatu. Wartość taka sama jak certyfikatu.  
  
- RSA. Podczas uzgadniania protokołu SSL WCF gwarantuje, że zdalnego punktu końcowego zawiera dokładnie klucza RSA, określone w tożsamości.  
  
 Jeśli usługa jest uwierzytelniany przy użyciu protokołu SSL z poziomu komunikatu lub transportu przy użyciu poświadczeń Windows do uwierzytelniania i negocjuje poświadczenie, następujące wartości tożsamości są prawidłowe:  
  
- DNS. Negocjacji przekazuje nazwę SPN usługi, dzięki czemu można sprawdzić nazwy DNS. Główna nazwa usługi jest w formie `host/<dns name>`.  
  
- SPN. Usługi jawne nazwy SPN jest zwracana, na przykład `host/myservice`.  
  
- UPN. Nazwa UPN konta usługi. Nazwa UPN jest w formie `username` @ `domain`. Na przykład, gdy usługa jest uruchomiona na koncie użytkownika, może być `username@contoso.com`.  
  
 Programowe określanie tożsamości (przy użyciu <xref:System.ServiceModel.EndpointAddress.Identity%2A> właściwość) jest opcjonalny. Jeśli nie określono żadnych tożsamości i typu poświadczeń klienta jest Windows, wartość domyślna to główna nazwa usługi z wartością ustawioną na część nazwy hosta z prefiksem adresu punktu końcowego usługi "hosta /" literału. Jeśli nie określono żadnych tożsamości i typu poświadczeń klienta jest certyfikatem, wartością domyślną jest `Certificate`. Dotyczy to zarówno zabezpieczenia na poziomie komunikatu i transportu.  
  
## <a name="identity-and-custom-bindings"></a>Tożsamość i powiązań niestandardowych  
 Ponieważ tożsamości usługi zależy od typu powiązania, używany, upewnij się, że odpowiednią tożsamość jest dostępne podczas tworzenia niestandardowego powiązania. Na przykład w poniższym przykładzie kodu tożsamości udostępniane nie jest zgodny z typem zabezpieczeń, ponieważ tożsamość dla powiązania uruchamiania bezpiecznej konwersacji nie pasuje do tożsamości dla powiązania w punkcie końcowym. Powiązanie bezpiecznej konwersacji ustawia tożsamość DNS, podczas gdy <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> ustawia tożsamość główna nazwa lub nazwy SPN.  
  
 [!code-csharp[C_Identity#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_identity/cs/source.cs#8)]
 [!code-vb[C_Identity#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_identity/vb/source.vb#8)]  
  
 Aby uzyskać więcej informacji o sposobie stosu powiązanie elementów poprawnie dla niestandardowego powiązania, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md). Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement>, zobacz [jak: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
- [Instrukcje: Tworzenie niestandardowego weryfikatora tożsamości klienta](../../../../docs/framework/wcf/extending/how-to-create-a-custom-client-identity-verifier.md)
- [Wybieranie typu poświadczeń](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Narzędzie do obsługi metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
- [Instrukcje: Pobieranie odcisku palca certyfikatu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
