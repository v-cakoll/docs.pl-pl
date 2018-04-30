---
title: Wybieranie typu poświadczeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae5eb9a10f438f1bb76c51c3c9da68273d94ab57
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="selecting-a-credential-type"></a>Wybieranie typu poświadczeń
*Poświadczenia* są dane [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] używa w celu ustalenia tożsamości lub funkcji. Na przykład usługi passport jest poświadczenia, który wystawia Rząd potwierdzenie możliwości dostępnych w kraju lub regionie. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], poświadczenia mogą mieć wiele form, takich jak tokeny nazwy użytkownika i certyfikaty X.509. W tym temacie omówiono poświadczeń, jak są używane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oraz sposobu wybierania prawo poświadczeń dla aplikacji.  
  
 W wielu innych krajów i regionów prawa jazdy jest przykładem poświadczenie. Licencji zawiera dane, które reprezentują tożsamość osoby i możliwości. Zawiera ona dowodu posiadania w formie obrazu właściciel. Licencji wystawiony przez zaufany urząd zwykle rządowych działu licencjonowania. Licencja jest zapieczętowany i może zawierać hologram, pokazujący, że nie został zmieniony przez niepowołane lub podrobić.  
  
 Umożliwienie korzystania z poświadczeń polega na prezentacji danych i dowodu posiadania danych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje różne typy poświadczeń na poziomie zabezpieczeń transportu i komunikatu. Na przykład, należy wziąć pod uwagę dwa typy obsługiwanych w poświadczeń [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: nazwa użytkownika oraz (X.509) certyfikatu poświadczeń.  
  
 Dla poświadczenie nazwy użytkownika tożsamości reprezentuje nazwę użytkownika i hasło zawiera dowodu posiadania. Zaufany urząd to w takim przypadku system, który sprawdza poprawność nazwy użytkownika i hasła.  
  
 Z poświadczeniami certyfikatu X.509, nazwa podmiotu i alternatywnej nazwy podmiotu określonych pól w ramach certyfikatu może służyć jako oświadczenia tożsamości podczas innych pól, takich jak `Valid From` i `Valid To` pól, określ ważności certyfikat.  
  
## <a name="transport-credential-types"></a>Typy poświadczenia transportu  
 W poniższej tabeli przedstawiono typy poświadczeń klienta, które mogą być używane przez powiązanie w tryb zabezpieczeń transport. Podczas tworzenia usługi należy skonfigurować `ClientCredentialType` właściwości do jednej z tych wartości, aby określić typ poświadczenia, które klient musi podać do komunikowania się z usługą. Typów można ustawić w plikach kodu lub konfiguracji.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient musi przedstawiać żadnego poświadczenia. Umożliwia to anonimowym klientem.|  
|Podstawowy|Określa uwierzytelnianie podstawowe dla klienta. Aby uzyskać dodatkowe informacje, zobacz RFC2617 —[uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego](http://go.microsoft.com/fwlink/?LinkID=88313).|  
|Skrót|Określa uwierzytelnianie szyfrowane dla klienta. Aby uzyskać dodatkowe informacje, zobacz RFC2617 —[uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego](http://go.microsoft.com/fwlink/?LinkID=88313).|  
|Uwierzytelnianie NTLM|Określa uwierzytelnianie NT LAN Manager (NTLM). To jest używany, gdy z jakiegoś powodu nie można użyć uwierzytelniania Kerberos. Można również wyłączyć jako rezerwowe, ustawiając <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> właściwości `false`, co powoduje, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dokonanie optymalnych zostać zgłoszony wyjątek, jeśli używane jest uwierzytelnianie NTLM. Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.|  
|Windows|Określa uwierzytelnianie systemu Windows. Aby określić tylko protokołu Kerberos w domenie systemu Windows, należy ustawić <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> właściwości `false` (wartość domyślna to `true`).|  
|certyfikat|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu X.509.|  
|Hasło|Użytkownik musi podać nazwę użytkownika i hasło. Sprawdź poprawność pary nazwa/hasło użytkownika za pomocą uwierzytelniania systemu Windows lub inne niestandardowe rozwiązanie.|  
  
### <a name="message-client-credential-types"></a>Typy poświadczeń klienta komunikatu  
 W poniższej tabeli przedstawiono typy możliwe poświadczeń, które można używać podczas tworzenia aplikacji, która korzysta z zabezpieczeń wiadomości. Te wartości można użyć w plikach kodu lub konfiguracji.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient musi przedstawiać poświadczeń. Umożliwia to anonimowym klientem.|  
|Windows|Umożliwia wymianę wiadomości SOAP występuje w kontekście zabezpieczeń ustanowione za pomocą poświadczeń systemu Windows.|  
|Nazwa użytkownika|Umożliwia usłudze wymagają uwierzytelnienia klienta z poświadczenie nazwy użytkownika. Należy pamiętać, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie zezwala na wszystkie operacje kryptograficzne z nazwami użytkowników, takich jak generowania podpis i szyfrowanie danych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia, że transport jest zabezpieczony, korzystając z poświadczeń nazwy użytkownika.|  
|certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu X.509.|  
|Wystawiony Token|Niestandardowy typ tokenu skonfigurowane zgodnie z zasadami zabezpieczeń. Domyślny typ tokenu to zabezpieczeń potwierdzenia Markup Language (SAML). Bezpieczne usługi tokenu wystawiła token. Aby uzyskać więcej informacji, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Model negocjacji poświadczenia usługi  
 *Negocjowanie* to proces ustanawiania relacji zaufania między klientem a usługą poprzez wymianę poświadczeń. Proces jest wykonywany wielokrotnie powtarzane między klientem i usługi, aby ujawnić tylko te informacje, które są niezbędne do następnego kroku w procesie negocjacji. W praktyce wynik końcowy jest dostarczanie poświadczeń usługi do klienta, który ma być używana podczas kolejnych operacji.  
  
 Z jednym wyjątkiem domyślnie powiązania dostarczane przez system w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie negocjowania poświadczeń usługi, korzystając z zabezpieczeniami na poziomie wiadomości. (Wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding>, który nie obsługuje zabezpieczeń domyślnie.) Aby wyłączyć to zachowanie, zobacz <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> i <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwości.  
  
> [!NOTE]
>  Gdy zabezpieczeń SSL jest używany z programem .NET Framework 3.5 lub nowszego oraz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient używa zarówno certyfikaty pośrednie w magazynie certyfikatów i certyfikaty pośrednie otrzymał podczas negocjacji w protokole SSL podczas weryfikacji łańcucha certyfikatu certyfikat usługi. .NET framework 3.0 używa tylko certyfikaty pośrednie zainstalowane w lokalnym magazynie certyfikatów.  
  
#### <a name="out-of-band-negotiation"></a>Negocjowanie poza pasmem  
 Po wyłączeniu automatycznej negocjacji poświadczenie usługi musi zainicjowana dla klienta przed wysłaniem komunikaty do usługi. Jest to nazywane również *poza pasmem* inicjowania obsługi administracyjnej. Na przykład jeśli określony typ poświadczeń jest certyfikatem, a automatyczne negocjacji jest wyłączone, klient musi skontaktować się Właściciel usługi do pobierania i instalowania certyfikatu na komputerze z uruchomionym aplikacji klienckiej. Można to zrobić, na przykład, jeśli chcesz ściśle kontrolować, które mogą uzyskać dostęp klienci usługi w scenariuszu business-to-business. Ten limit z-poza pasmem — negocjowanie może odbywać się w wiadomości e-mail, a certyfikat X.509 jest przechowywany w magazynie certyfikatów systemu Windows, przy użyciu narzędzia, takiego jak przystawki Certyfikaty programu Microsoft Management Console (MMC).  
  
> [!NOTE]
>  <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwość jest używana do świadczenia usług przy użyciu certyfikatu, który został osiągnięty na negocjacji poza pasmem. Jest to konieczne, korzystając z <xref:System.ServiceModel.BasicHttpBinding> klasy, ponieważ powiązanie nie zezwala na automatyczne negocjacji. Właściwość również jest używany w scenariuszu nieskorelowane dupleksowych. Jest scenariusz, w którym serwer wysyła wiadomość do klienta bez konieczności klient najpierw wysłać żądania do serwera. Ponieważ serwer nie ma żądanie od klienta, należy użyć certyfikat klienta do szyfrowania wiadomości do klienta.  
  
## <a name="setting-credential-values"></a>Ustawienie wartości poświadczeń  
 Po wybraniu trybu zabezpieczeń, należy określić poświadczenia rzeczywistego. Na przykład jeśli typ poświadczeń jest ustawiony na "certyfikatów", następnie należy skojarzyć poświadczenie (na przykład określonego certyfikatu X.509) z usługi lub klienta.  
  
 W zależności od tego, czy są programowania usługi lub klienta Metoda ustawiania wartości poświadczeń różni się nieznacznie.  
  
### <a name="setting-service-credentials"></a>Ustawienie poświadczeń usługi  
 Jeśli używasz trybu transportu i są przy użyciu protokołu HTTP jako transportu, możesz użyć albo Internet Information Services (IIS), lub konfigurowanie portu z certyfikatem. Aby uzyskać więcej informacji, zobacz [Przegląd zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) i [zabezpieczeń transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby udostępnić usługi za pomocą poświadczeń w kodzie, Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy i określ odpowiednie poświadczenia, za pomocą <xref:System.ServiceModel.Description.ServiceCredentials> klasy dostępne za pośrednictwem <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.  
  
#### <a name="setting-a-certificate"></a>Ustawienia certyfikatu  
 Aby udostępnić usługi za pomocą certyfikatu X.509, który ma być używany do uwierzytelniania usługi dla klientów, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy.  
  
 Aby udostępnić usługi o certyfikat klienta, należy użyć <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential> klasy.  
  
#### <a name="setting-windows-credentials"></a>Ustawienie poświadczeń systemu Windows  
 Jeśli klient określa prawidłową nazwę użytkownika i hasło, to poświadczenie jest używane do uwierzytelniania klienta. W przeciwnym razie używane są poświadczenia bieżącego zalogowanego użytkownika.  
  
### <a name="setting-client-credentials"></a>Ustawianie poświadczeń klienta  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], użyj aplikacji klienckich [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, aby połączyć się z usługami. Każdy klient pochodzi z <xref:System.ServiceModel.ClientBase%601> klasy i <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> na kliencie umożliwia określenie różnych wartości poświadczeń klienta.  
  
#### <a name="setting-a-certificate"></a>Ustawienia certyfikatu  
 Aby udostępnić usługi za pomocą certyfikatu X.509, który jest używany do uwierzytelniania klienta do usługi, użyj <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> klasy.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Jak poświadczeń klienta są używane do uwierzytelniania klienta do usługi  
 Klient poświadczenia wymagane do komunikacji z usługą informacje przy użyciu <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwości lub <xref:System.ServiceModel.ChannelFactory.Credentials%2A> właściwości. Bezpieczny kanał używa tych informacji do uwierzytelniania klienta do usługi. Uwierzytelnianie jest przeprowadzane za pomocą jednego z dwóch trybów:  
  
-   Przed wysłaniem pierwszego komunikatu przy użyciu poświadczeń klienta są używane raz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wystąpienie klienta, aby ustanowić kontekst zabezpieczeń. Wszystkie komunikaty aplikacji są następnie zabezpieczone za pomocą kontekstu zabezpieczeń.  
  
-   Poświadczenia klienta są używane do uwierzytelniania każdej wiadomości aplikacji wysyłane do usługi. W takim przypadku kontekst nie zostanie nawiązane między klientem a usługą.  
  
### <a name="established-identities-cannot-be-changed"></a>Nie można zmienić tożsamości ustalonych  
 W przypadku pierwsza metoda ustalonym kontekstem jest stałe skojarzone z tożsamością klienta. Oznacza to, że po ustanowieniu kontekstu zabezpieczeń nie można zmienić tożsamość skojarzoną z klienta.  
  
> [!IMPORTANT]
>  Istnieje sytuacja pod uwagę podczas tożsamości nie można przełączyć (to znaczy podczas ustanawiania zabezpieczeń kontekstu jest włączona, domyślnie). Po utworzeniu usługi, która komunikuje się z usługą drugi tożsamość użyty do otwarcia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta drugi usługi nie można zmienić. To stanie się problemem, jeśli wielu klientów mogą korzystać z pierwszej usługi i usługa personifikuje klientów podczas uzyskiwania dostępu do usługi drugiego. Jeśli usługa ponownie używa tego samego klienta dla wszystkich obiektów wywołujących, wszystkie połączenia z usługą drugi są wykonywane z tożsamością pierwszy obiekt wywołujący, który został użyty do otwarcia klienta usługi drugiego. Innymi słowy usługa używa tożsamości pierwszego klienta dla wszystkich klientów do komunikacji z usługą drugiego. Może to spowodować podniesienie uprawnień. Jeśli nie jest zamierzone zachowanie usługi, musi śledzić każdy obiekt wywołujący i tworzenia nowego klienta do drugiego usługi dla każdego obiektu wywołującego w odrębnych i upewnić, że usługa używa tylko prawo klienta do obiektu wywołującego w prawo do komunikowania się z usługą drugiego.  
  
 Aby uzyskać więcej informacji na temat poświadczeń i bezpieczne sesje, zobacz [zagadnienia dotyczące zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
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
