---
title: Wybieranie typu poświadczeń
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: c2ee1b9062d14eaa44de0651985c2a385fe02f8e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503394"
---
# <a name="selecting-a-credential-type"></a>Wybieranie typu poświadczeń
*Poświadczenia* jest Windows Communication Foundation (WCF) używanych do ustalenia tożsamości lub możliwości danych. Na przykład usługi passport jest poświadczeń, przez Rząd potwierdzenie zaawansowanych możliwości dostępnych w kraju lub regionie. W programie WCF poświadczenia mogą mieć wiele form, takich jak tokeny nazwy użytkownika i certyfikaty X.509. W tym temacie omówiono poświadczenia, jak są używane w programie WCF i jak wybierać odpowiednie poświadczenia dla aplikacji.  
  
 W wielu krajach i regionach prawa jazdy jest przykładem poświadczenia. Licencja zawiera dane, które reprezentuje tożsamość osoby i możliwości. Zawiera ono dowód przesyłany w postaci obrazu inicjator. Licencja jest wystawiony przez zaufany urząd, zwykle rządowych działu licencjonowania. Licencja jest zapieczętowany i może zawierać hologram, pokazujący, że nie został zmodyfikowany lub podrobić.  
  
 Umożliwienie korzystania z poświadczeń obejmuje prezentowanie danych i dowodu posiadania danych. Usługi WCF obsługuje różne typy poświadczeń na poziomach zabezpieczeń transportu i komunikatu. Na przykład, należy wziąć pod uwagę dwa typy obsługiwanych w programie WCF poświadczeń: nazwa użytkownika oraz (X.509) certyfikatu poświadczeń.  
  
 Poświadczenie nazwy użytkownika, aby uzyskać nazwę użytkownika reprezentuje tożsamości, a hasło zawiera dowodu posiadania. Zaufany urząd w tym przypadku to system, który sprawdza poprawność nazwy użytkownika i hasła.  
  
 Przy użyciu poświadczeń certyfikatu X.509, nazwa podmiotu i alternatywna nazwa podmiotu określonych pól w ramach certyfikatu może służyć jako oświadczenia tożsamości podczas inne pola, takie jak `Valid From` i `Valid To` pola, określają ważności certyfikat.  
  
## <a name="transport-credential-types"></a>Typy poświadczeń transportu  
 W poniższej tabeli przedstawiono typy poświadczeń klienta, które mogą być używane przez powiązanie w tryb zabezpieczeń transport. Podczas tworzenia usługi, ustaw `ClientCredentialType` właściwości do jednej z tych wartości, aby określić typ poświadczeń, które klient musi podać do komunikowania się z Twoją usługą. Możesz ustawić typy w plikach kodu lub konfiguracji.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, klient musi przedstawić żadnych poświadczeń. Przekłada się to anonimowym klientem.|  
|Podstawowy|Określa uwierzytelnianie podstawowe dla klienta. Aby uzyskać więcej informacji, zobacz RFC2617 —[uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|Podsumowanie|Określa, uwierzytelniania szyfrowanego dla klienta. Aby uzyskać więcej informacji, zobacz RFC2617 —[uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane](https://go.microsoft.com/fwlink/?LinkID=88313).|  
|Uwierzytelnianie NTLM|Określa uwierzytelniania NT LAN Manager (NTLM). To jest używany, gdy z jakiegoś powodu nie można użyć uwierzytelniania Kerberos. Można również wyłączyć, ustawiając jako rezerwowe <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> właściwości `false`, co powoduje, że WCF umożliwiają staranności do zgłoszenia wyjątku, jeśli używane jest uwierzytelnianie NTLM. Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.|  
|Windows|Określa uwierzytelniania Windows. Aby określić protokołu Kerberos w domenie Windows, należy ustawić <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> właściwości `false` (wartość domyślna to `true`).|  
|Certyfikat|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu X.509.|  
|Hasło|Użytkownik musi podać nazwę użytkownika i hasło. Sprawdź poprawność pary nazwa/hasło użytkownika za pomocą uwierzytelniania Windows lub inne niestandardowe rozwiązanie.|  
  
### <a name="message-client-credential-types"></a>Typy poświadczeń klienta wiadomości  
 W poniższej tabeli przedstawiono typy możliwe poświadczeń, których można używać podczas tworzenia aplikacji, która używa zabezpieczenia komunikatów. Te wartości można użyć w plikach kodu lub konfiguracji.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient nie potrzebuje do przedstawienia poświadczeń. Przekłada się to anonimowym klientem.|  
|Windows|Umożliwia wymianę komunikatów SOAP występuje w kontekście zabezpieczeń, nawiązane przy użyciu poświadczeń Windows.|  
|Nazwa użytkownika|Umożliwia usłudze wymagają uwierzytelnienia klienta za pomocą poświadczenie nazwy użytkownika. Należy pamiętać, usługi WCF nie zezwala na wszystkie operacje kryptograficzne przy użyciu nazwy użytkownika, takie jak generowania podpisu i szyfrowania danych. Usługi WCF zapewnia, że transportu jest zabezpieczony przy użyciu poświadczeń nazwy użytkownika.|  
|Certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu X.509.|  
|Wystawiony Token|Niestandardowy typ tokenu skonfigurowane zgodnie z zasadami zabezpieczeń. Domyślny typ tokenu jest zabezpieczeń potwierdzenia Markup Language (SAML). Token wystawiony przez usługa bezpiecznych tokenów. Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Model negocjowania poświadczeń usługi  
 *Negocjowanie* polega na ustanawianie relacji zaufania między klientem a usługą przez wymianę poświadczeń. Ten proces odbywa się interakcyjnie między klientem a service, tak, aby ujawnić tylko informacje niezbędne do następnego kroku w procesie negocjacji. W praktyce efekt jest dostarczenie poświadczeń usługi do klienta, który ma być używany podczas kolejnych operacji.  
  
 Z jednym wyjątkiem domyślnie powiązania dostarczane przez system w usłudze WCF negocjowania poświadczeń usługi automatycznie przy użyciu zabezpieczeń na poziomie komunikatu. (Wyjątek stanowi <xref:System.ServiceModel.BasicHttpBinding>, który nie obsługuje zabezpieczeń domyślnie.) Aby wyłączyć to zachowanie, zobacz <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> i <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwości.  
  
> [!NOTE]
>  Stosowania zabezpieczeń SSL za pomocą programu .NET Framework 3.5 lub nowszy klient WCF używa zarówno certyfikaty pośrednie w magazynie certyfikatów i certyfikaty pośrednie odebranych podczas negocjacji w protokole SSL podczas weryfikacji łańcucha certyfikatu usługi certyfikat. .NET framework 3.0 używa tylko certyfikaty pośrednie zainstalowany w lokalnym magazynie certyfikatów.  
  
#### <a name="out-of-band-negotiation"></a>Negocjowanie poza pasmem  
 Po wyłączeniu automatycznego negocjowania poświadczeń usługi musi być obsługiwana po stronie klienta przed wysłaniem komunikatów do usługi. Jest to nazywane również *out-of-band* inicjowania obsługi administracyjnej. Na przykład określony typ poświadczeń jest to certyfikat, i automatyczne negocjowanie jest wyłączone, klient powinni skontaktować się ze Właściciel usługi do odbierania i zainstaluj certyfikat na komputerze z uruchomioną aplikacją klienta. Można to zrobić, na przykład, jeśli chcesz ściśle kontrolować, którzy klienci uzyskaniem dostępu do usług w ramach scenariusza business-to-business. Ten limit z — poza pasmem negocjacja może odbywać się w wiadomości e-mail, a certyfikat X.509 jest przechowywany w magazynie certyfikatów Windows, za pomocą narzędzia takiego jak przystawki Certyfikaty programu Microsoft Management Console (MMC).  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość jest używana do świadczenia usług przy użyciu certyfikatu, który został osiągnięty przy użyciu negocjacji poza pasmem. Jest to konieczne, korzystając z <xref:System.ServiceModel.BasicHttpBinding> klasy, ponieważ powiązanie nie zezwala na automatyczne negocjacji. Jest również używana w scenariuszu nieskorelowane dwukierunkowego. Jest to scenariusz, w której serwer wysyła wiadomość do klienta bez konieczności klienta najpierw wysyłać żądania do serwera. Ponieważ serwer nie ma żądania od klienta, ona używać certyfikat klienta do szyfrowania wiadomości do klienta.  
  
## <a name="setting-credential-values"></a>Ustawienie wartości poświadczeń  
 Po wybraniu tryb zabezpieczeń, należy określić rzeczywisty poświadczeń. Na przykład jeśli typ poświadczeń jest ustawiony na "certyfikatu", następnie należy skojarzyć poświadczenie (na przykład określonego certyfikatu X.509) przy użyciu usługi lub klienta.  
  
 W zależności od tego, czy programujesz, usługi lub klienta metoda do ustawiania wartości poświadczenie różni się nieco.  
  
### <a name="setting-service-credentials"></a>Ustawienie poświadczeń usługi  
 Jeśli używasz trybu transportu i korzystania z protokołu HTTP jako transportu, możesz użyć albo Internet Information Services (IIS), lub konfigurowanie portu z certyfikatem. Aby uzyskać więcej informacji, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) i [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby udostępnić usługę przy użyciu poświadczeń w kodzie, Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy i określ odpowiednie poświadczenia, za pomocą <xref:System.ServiceModel.Description.ServiceCredentials> klasy, dostępne za pośrednictwem <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.  
  
#### <a name="setting-a-certificate"></a>Ustawienia certyfikatu  
 Aby zainicjować obsługę usługi za pomocą certyfikatu X.509, który ma być używany do uwierzytelniania usługi dla klientów, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy.  
  
 Aby zainicjować obsługę usługi za pomocą certyfikatu klienta, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> klasy.  
  
#### <a name="setting-windows-credentials"></a>Ustawianie poświadczeń Windows  
 Jeśli klient określa prawidłową nazwę użytkownika i hasło, że poświadczenie jest używane do uwierzytelniania klienta. W przeciwnym razie używane są poświadczenia bieżącego zalogowanego użytkownika.  
  
### <a name="setting-client-credentials"></a>Ustawianie poświadczeń klienta  
 W programie WCF aplikacji klienckich, należy użyć klienta programu WCF łączenie się z usługami. Każdy klient pochodzi z <xref:System.ServiceModel.ClientBase%601> klasy, a <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwości na komputerze klienckim umożliwia określenie różnych wartości poświadczeń klienta.  
  
#### <a name="setting-a-certificate"></a>Ustawienia certyfikatu  
 Aby zainicjować obsługę usługi za pomocą certyfikatu X.509, który jest używany do uwierzytelniania klienta do usługi, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Sposób używania poświadczeń klienta do uwierzytelniania klienta do usługi  
 Wymagany do komunikowania się z usługą informacji o poświadczeniach klienta znajduje się za pomocą <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwości lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> właściwości. Kanał zabezpieczeń używa tych informacji do uwierzytelniania klienta do usługi. Uwierzytelnianie odbywa się za pomocą jednego z dwóch trybów:  
  
-   Poświadczenia klienta są używane raz przed wysłaniem pierwszy komunikat przy użyciu wystąpienia klienta programu WCF do ustanawiania kontekstu zabezpieczeń. Wszystkie komunikaty aplikacji są następnie zabezpieczone za pomocą kontekstu zabezpieczeń.  
  
-   Poświadczenia klienta są używane do uwierzytelniania każdego komunikatu aplikacji wysyłane do usługi. W tym przypadku kontekst nie zostanie nawiązane między klientem a usługą.  
  
### <a name="established-identities-cannot-be-changed"></a>Nie można zmienić tożsamości ustalonych  
 W przypadku pierwszej metody ustanowionych kontekst jest stałe skojarzone z tożsamością klienta. Oznacza to, że po ustanowieniu kontekstu zabezpieczeń, nie można zmienić na tożsamość skojarzoną z klienta.  
  
> [!IMPORTANT]
>  Istnieje sytuacja, aby wiedzieć, kiedy nie mogą być przełączane tożsamości (oznacza to, kiedy ustanowienia zabezpieczeń kontekstu jest włączona, domyślne zachowanie). Jeśli tworzysz to usługa, która komunikuje się z usługą drugi, nie można zmienić tożsamości używany do otwierania klienta platformy WCF do drugiego usługi. Ten staje się problemem, jeśli wielu klientów mogą korzystać z pierwszej usługi i usługa personifikuje klientów podczas uzyskiwania dostępu do drugiego usługi. Jeśli usługa używa tego samego klienta dla wszystkich obiektów wywołujących, wszystkie wywołania do drugiego usługi są wykonywane z tożsamością pierwszy obiekt wywołujący, który został użyty do otwierania klienta do drugiego usługi. Innymi słowy usługa korzysta z tożsamości pierwszy klient dla swoich klientów do komunikacji z usługą drugiego. Może to prowadzić do podniesienia uprawnień. Jeśli nie jest to zachowanie usługi, należy śledzić każdy obiekt wywołujący i tworzenia nowego klienta do drugiego usługi co różne obiektu wywołującego i upewnij się, że usługa używa tylko odpowiednie klienta do obiektu wywołującego w prawo do komunikacji z usługą drugi.  
  
 Aby uzyskać więcej informacji na temat poświadczeń i bezpieczne sesje, zobacz [zagadnienia dotyczące zabezpieczeń bezpiecznych sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
