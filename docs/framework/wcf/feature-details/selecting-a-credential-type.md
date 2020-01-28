---
title: Wybieranie typu poświadczeń
ms.date: 03/30/2017
ms.assetid: bf707063-3f30-4304-ab53-0e63413728a8
ms.openlocfilehash: 6737f7daeb37e2e296ca0429d73b963743c409a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746143"
---
# <a name="selecting-a-credential-type"></a>Wybieranie typu poświadczeń
*Poświadczenia* to Windows Communication Foundation danych (WCF) służących do ustanowienia zatwierdzono tożsamości lub możliwości. Na przykład usługa Passport jest poświadczeniem instytucji rządowych, aby potwierdzić obywatelstwo w kraju lub regionie. W programie WCF poświadczenia mogą przyjmować wiele form, takich jak tokeny nazw użytkowników i certyfikaty X. 509. W tym temacie omówiono poświadczenia, sposób ich używania w programie WCF oraz sposób wybierania odpowiednich poświadczeń dla aplikacji.  
  
 W wielu krajach i regionach licencja sterownika jest przykładem poświadczenia. Licencja zawiera dane reprezentujące tożsamość i możliwości osoby. Zawiera dowód posiadania w postaci obrazu posiadacza. Licencja jest wystawiana przez zaufany urząd, zazwyczaj przez rządową Departament licencjonowania. Licencja jest zapieczętowana i może zawierać hologram, co oznacza, że nie została naruszona ani sfałszowana.  
  
 Przedstawienie poświadczeń obejmuje przedstawienie danych i potwierdzenie posiadania danych. Usługa WCF obsługuje różne typy poświadczeń zarówno na poziomie zabezpieczeń transportu, jak i komunikatów. Rozważmy na przykład dwa typy poświadczeń obsługiwane w programie WCF: Nazwa użytkownika i (X. 509) poświadczenia certyfikatu.  
  
 W przypadku poświadczenia nazwy użytkownika nazwa użytkownika reprezentuje zażądaną tożsamość, a hasło zapewnia dowód posiadania. W tym przypadku zaufany urząd sprawdza poprawność nazwy użytkownika i hasła.  
  
 Za pomocą poświadczeń certyfikatu X. 509 nazwa podmiotu, alternatywna nazwa podmiotu lub określone pola w ramach certyfikatu mogą być używane jako oświadczenia tożsamości, natomiast inne pola, takie jak `Valid From` i `Valid To`, określają ważność certyfikatu.  
  
## <a name="transport-credential-types"></a>Typy poświadczeń transportu  
 W poniższej tabeli przedstawiono możliwe typy poświadczeń klienta, które mogą być używane przez powiązanie w trybie zabezpieczenia transportu. Podczas tworzenia usługi ustaw właściwość `ClientCredentialType` na jedną z tych wartości, aby określić typ poświadczenia, które klient musi podać, aby komunikować się z usługą. Można ustawić typy w plikach kodu lub konfiguracji.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient nie musi zaprezentować żadnego poświadczenia. Powoduje to przetłumaczenie na klienta anonimowego.|  
|Podstawowy|Określa podstawowe uwierzytelnianie klienta. Aby uzyskać dodatkowe informacje, zobacz RFC2617 — uwierzytelnianie[http: uwierzytelnianie podstawowe i szyfrowane](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|Szyfrowane|Określa uwierzytelnianie szyfrowane dla klienta. Aby uzyskać dodatkowe informacje, zobacz RFC2617 — uwierzytelnianie[http: uwierzytelnianie podstawowe i szyfrowane](ftp://ftp.rfc-editor.org/in-notes/rfc2617.txt).|  
|NTLM|Określa uwierzytelnianie NT LAN Manager (NTLM). Jest on używany, jeśli z jakiegoś powodu nie można użyć uwierzytelniania Kerberos. Możesz również wyłączyć jego użycie jako rezerwę, ustawiając właściwość <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> na `false`, co powoduje, że program WCF będzie najlepszym nakładem na zgłoszenie wyjątku w przypadku użycia protokołu NTLM. Należy pamiętać, że ustawienie tej właściwości na `false` może nie uniemożliwiać wysyłania poświadczeń NTLM za pośrednictwem sieci.|  
|Windows|Określa uwierzytelnianie systemu Windows. Aby określić tylko protokół Kerberos w domenie systemu Windows, ustaw właściwość <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> na `false` (wartość domyślna to `true`).|  
|Certyfikat|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu X. 509.|  
|Hasło|Użytkownik musi podać nazwę użytkownika i hasło. Sprawdź poprawność pary nazwa użytkownika/hasło przy użyciu uwierzytelniania systemu Windows lub innego niestandardowego rozwiązania.|  
  
### <a name="message-client-credential-types"></a>Typy poświadczeń klienta wiadomości  
 W poniższej tabeli przedstawiono możliwe typy poświadczeń, których można użyć podczas tworzenia aplikacji, która korzysta z zabezpieczeń komunikatów. Tych wartości można użyć w plikach kodu lub konfiguracji.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient nie musi przedstawić poświadczenia. Powoduje to przetłumaczenie na klienta anonimowego.|  
|Windows|Zezwala wymianie komunikatów protokołu SOAP w kontekście zabezpieczeń ustanowionym przy użyciu poświadczeń systemu Windows.|  
|Nazwa użytkownika|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu poświadczeń nazwy użytkownika. Należy pamiętać, że WCF nie zezwala na operacje kryptograficzne z nazwami użytkowników, takie jak generowanie podpisu lub szyfrowanie danych. Usługa WCF gwarantuje, że transport jest zabezpieczony przy użyciu poświadczeń nazwy użytkownika.|  
|Certyfikat|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu certyfikatu X. 509.|  
|Wystawiony token|Typ niestandardowego tokenu skonfigurowany zgodnie z zasadami zabezpieczeń. Domyślnym typem tokenu jest język SAML (Security Assertions Markup Language). Token jest wystawiony przez usługę bezpiecznego tokenu. Aby uzyskać więcej informacji, zobacz [federacyjne i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="negotiation-model-of-service-credentials"></a>Model negocjacji poświadczeń usługi  
 *Negocjowanie* to proces ustanawiania relacji zaufania między klientem a usługą przez wymianę poświadczeń. Proces jest wykonywany w sposób iteracyjny między klientem a usługą, dlatego w celu ujawnienia tylko informacji niezbędnych do następnego kroku procesu negocjacji. W rzeczywistości wynik końcowy to dostarczenie poświadczeń usługi do klienta, który będzie używany w kolejnych operacjach.  
  
 Z jednym wyjątkiem domyślnie powiązania udostępnione przez system w programie WCF negocjują poświadczenia usługi automatycznie w przypadku korzystania z zabezpieczeń na poziomie komunikatów. (Wyjątkiem jest <xref:System.ServiceModel.BasicHttpBinding>, które domyślnie nie włącza zabezpieczeń). Aby wyłączyć to zachowanie, zobacz Właściwości <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> i <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A>.  
  
> [!NOTE]
> Gdy zabezpieczenia SSL są używane w .NET Framework 3,5 i nowszych, klient programu WCF używa zarówno certyfikatów pośrednich w magazynie certyfikatów, jak i pośrednich certyfikatów odebranych podczas negocjowania protokołu SSL w celu przeprowadzenia walidacji łańcucha certyfikatów w usłudze certyfikatu. .NET Framework 3,0 używa tylko certyfikatów pośrednich zainstalowanych w lokalnym magazynie certyfikatów.  
  
#### <a name="out-of-band-negotiation"></a>Negocjowanie poza pasmem  
 Jeśli automatyczne negocjowanie jest wyłączone, poświadczenia usługi muszą zostać wdrożone na kliencie przed wysłaniem jakichkolwiek komunikatów do usługi. Jest to również znane jako inicjowanie obsługi *poza pasmem* . Na przykład jeśli określony typ poświadczeń jest certyfikatem, a automatyczne negocjowanie jest wyłączone, klient musi skontaktować się z właścicielem usługi, aby odebrać i zainstalować certyfikat na komputerze z uruchomioną aplikacją kliencką. Można to zrobić na przykład wtedy, gdy użytkownik chce ściśle kontrolować, którzy klienci mogą uzyskać dostęp do usługi w scenariuszu biznesowym. Takie negocjowanie poza pasmem można wykonać w wiadomości e-mail, a certyfikat X. 509 jest przechowywany w magazynie certyfikatów systemu Windows przy użyciu narzędzia, takiego jak Przystawka Certyfikaty programu Microsoft Management Console (MMC).  
  
> [!NOTE]
> Właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> służy do świadczenia usługi przy użyciu certyfikatu, który został osiągnięty za pomocą negocjacji poza pasmem. Jest to konieczne w przypadku używania klasy <xref:System.ServiceModel.BasicHttpBinding>, ponieważ powiązanie nie zezwala na automatyczne negocjowanie. Właściwość jest również używana w nieskorelowanym scenariuszu dupleksu. Jest to scenariusz, w którym serwer wysyła komunikat do klienta bez konieczności uprzedniego wysłania żądania do serwera. Ponieważ serwer nie ma żądania od klienta, musi użyć certyfikatu klienta, aby zaszyfrować komunikat na kliencie.  
  
## <a name="setting-credential-values"></a>Ustawianie wartości poświadczeń  
 Po wybraniu trybu zabezpieczeń należy określić rzeczywiste poświadczenia. Na przykład, jeśli typ poświadczenia ma wartość "certyfikat", należy skojarzyć określone poświadczenie (na przykład certyfikat X. 509) z usługą lub klientem.  
  
 W zależności od tego, czy program korzysta z usługi, czy klienta, metoda ustawiania wartości poświadczeń różni się nieco.  
  
### <a name="setting-service-credentials"></a>Ustawianie poświadczeń usługi  
 Jeśli używasz trybu transportu i używasz protokołu HTTP jako transportu, musisz użyć obu Internet Information Services (IIS) lub skonfigurować port przy użyciu certyfikatu. Aby uzyskać więcej informacji, zobacz [Omówienie zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md) i [zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Aby zainicjować obsługę administracyjną usługi przy użyciu poświadczeń w kodzie, Utwórz wystąpienie klasy <xref:System.ServiceModel.ServiceHost> i określ odpowiednie poświadczenie przy użyciu klasy <xref:System.ServiceModel.Description.ServiceCredentials>, dostępnym za pośrednictwem właściwości <xref:System.ServiceModel.ServiceHostBase.Credentials%2A>.  
  
#### <a name="setting-a-certificate"></a>Ustawianie certyfikatu  
 Aby zainicjować obsługę administracyjną usługi z certyfikatem X. 509 do użycia w celu uwierzytelnienia usługi dla klientów, użyj metody <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A> klasy <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>.  
  
 Aby zainicjować obsługę administracyjną usługi przy użyciu certyfikatu klienta, należy użyć metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> klasy <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>.  
  
#### <a name="setting-windows-credentials"></a>Ustawianie poświadczeń systemu Windows  
 Jeśli klient określi prawidłową nazwę użytkownika i hasło, to poświadczenie jest używane do uwierzytelniania klienta. W przeciwnym razie używane są poświadczenia bieżącego zalogowanego użytkownika.  
  
### <a name="setting-client-credentials"></a>Ustawianie poświadczeń klienta  
 W programie WCF aplikacje klienckie używają klienta WCF do łączenia się z usługami. Każdy klient pochodzi z klasy <xref:System.ServiceModel.ClientBase%601>, a właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> na kliencie umożliwia określenie różnych wartości poświadczeń klienta.  
  
#### <a name="setting-a-certificate"></a>Ustawianie certyfikatu  
 Aby zainicjować obsługę administracyjną dla usługi za pomocą certyfikatu X. 509, który jest używany do uwierzytelniania klienta w usłudze, użyj metody <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> klasy <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>.  
  
## <a name="how-client-credentials-are-used-to-authenticate-a-client-to-the-service"></a>Jak poświadczenia klienta są używane do uwierzytelniania klienta w usłudze  
 Informacje o poświadczeniach klienta wymagane do komunikacji z usługą są udostępniane przy użyciu właściwości <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> lub właściwości <xref:System.ServiceModel.ChannelFactory.Credentials%2A>. Kanał zabezpieczeń używa tych informacji do uwierzytelniania klienta w usłudze. Uwierzytelnianie odbywa się przy użyciu jednego z dwóch trybów:  
  
- Poświadczenia klienta są używane raz przed wysłaniem pierwszej wiadomości, przy użyciu wystąpienia klienta programu WCF do ustanowienia kontekstu zabezpieczeń. Wszystkie komunikaty aplikacji są następnie zabezpieczone za pomocą kontekstu zabezpieczeń.  
  
- Poświadczenia klienta służą do uwierzytelniania wszystkich komunikatów aplikacji wysyłanych do usługi. W takim przypadku nie ustanowiono kontekstu między klientem a usługą.  
  
### <a name="established-identities-cannot-be-changed"></a>Nie można zmienić ustanowionych tożsamości  
 Gdy pierwsza metoda jest używana, ustanowiony kontekst jest trwale skojarzony z tożsamością klienta. Oznacza to, że po ustanowieniu kontekstu zabezpieczeń tożsamość skojarzona z klientem nie może zostać zmieniona.  
  
> [!IMPORTANT]
> Istnieje konieczność, aby mieć świadomość, kiedy nie można przełączyć tożsamości (to oznacza, że po włączeniu kontekstu zabezpieczeń, zachowanie domyślne). Jeśli utworzysz usługę, która komunikuje się z drugą usługą, nie można zmienić tożsamości użytej do otwarcia klienta programu WCF w drugiej usłudze. Jest to problem, jeśli wielu klientów może korzystać z pierwszej usługi, a usługa personifikuje klientów podczas uzyskiwania dostępu do drugiej usługi. Jeśli usługa ponownie używa tego samego klienta dla wszystkich wywołujących, wszystkie wywołania drugiej usługi są wykonywane w ramach tożsamości pierwszego obiektu wywołującego, który został użyty do otwarcia klienta w drugiej usłudze. Innymi słowy, usługa używa tożsamości pierwszego klienta dla wszystkich klientów do komunikowania się z drugą usługą. Może to prowadzić do podniesienia uprawnień. Jeśli nie jest to wymagane zachowanie usługi, należy śledzić każdego wywołującego i utworzyć nowego klienta do drugiej usługi dla każdego oddzielnego obiektu wywołującego oraz upewnić się, że usługa używa tylko odpowiedniego klienta dla właściwego wywołującego, aby komunikować się z drugą usługą.  
  
 Aby uzyskać więcej informacji o poświadczeniach i bezpiecznych sesjach, zobacz [zagadnienia dotyczące zabezpieczeń bezpiecznych sesji](../../../../docs/framework/wcf/feature-details/security-considerations-for-secure-sessions.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverMsmq.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A?displayProperty=nameWithType>
- [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Programowanie zabezpieczeń WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [Zabezpieczenia transportu HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
