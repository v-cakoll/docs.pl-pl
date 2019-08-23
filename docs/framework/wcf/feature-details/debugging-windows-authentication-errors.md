---
title: Debugowanie błędów uwierzytelniania systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: 20ca8f049298f75412da4c8a7e58975954f67741
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968857"
---
# <a name="debugging-windows-authentication-errors"></a>Debugowanie błędów uwierzytelniania systemu Windows
W przypadku korzystania z uwierzytelniania systemu Windows jako mechanizmu zabezpieczeń interfejs dostawcy obsługi zabezpieczeń (SSPI) obsługuje procesy zabezpieczeń. Gdy w warstwie SSPI wystąpią błędy zabezpieczeń, są one nałożone przez Windows Communication Foundation (WCF). Ten temat zawiera informacje o strukturze i zestawie pytań ułatwiających zdiagnozowanie błędów.  
  
 Aby zapoznać się z omówieniem protokołu Kerberos, zobacz Omówienie protokołu [Kerberos](https://go.microsoft.com/fwlink/?LinkID=86946). Aby zapoznać się z omówieniem interfejsu SSPI, zobacz [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 W przypadku uwierzytelniania systemu Windows funkcja WCF zazwyczaj używa dostawcy usługi negocjowania zabezpieczeń (SSP), który wykonuje wzajemne uwierzytelnianie Kerberos między klientem a usługą. Jeśli protokół Kerberos nie jest dostępny, domyślnie WCF powraca do programu NT LAN Manager (NTLM). Można jednak skonfigurować funkcję WCF do używania tylko protokołu Kerberos (i zgłosić wyjątek, jeśli protokół Kerberos nie jest dostępny). Istnieje również możliwość skonfigurowania programu WCF do korzystania z ograniczonych form protokołu Kerberos.  
  
## <a name="debugging-methodology"></a>Metodologia debugowania  
 Podstawowa metoda jest następująca:  
  
1. Określ, czy używasz uwierzytelniania systemu Windows. Jeśli używasz innego schematu, ten temat nie ma zastosowania.  
  
2. Jeśli masz pewność, że używasz uwierzytelniania systemu Windows, ustal, czy konfiguracja usługi WCF korzysta z protokołu Kerberos Direct czy z negocjowaniem.  
  
3. Po ustaleniu, czy konfiguracja używa protokołu Kerberos lub NTLM, można zrozumieć komunikaty o błędach w poprawnym kontekście.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Dostępność protokołu Kerberos i NTLM  
 Dostawca SSP Kerberos wymaga, aby kontroler domeny działał jako centrum dystrybucji kluczy Kerberos (KDC). Protokół Kerberos jest dostępny tylko wtedy, gdy zarówno klient, jak i usługa korzystają z tożsamości domeny. W przypadku innych kombinacji kont używane jest uwierzytelnianie NTLM, zgodnie z podsumowaniem w poniższej tabeli.  
  
 Nagłówki tabeli zawierają możliwe typy kont używane przez serwer. W lewej kolumnie są wyświetlane możliwe typy kont używane przez klienta programu.  
  
||Użytkownik lokalny|System lokalny|Użytkownik domeny|Komputer domeny|  
|-|----------------|------------------|-----------------|--------------------|  
|Użytkownik lokalny|NTLM|NTLM|NTLM|NTLM|  
|System lokalny|Anonimowe uwierzytelnianie NTLM|Anonimowe uwierzytelnianie NTLM|Anonimowe uwierzytelnianie NTLM|Anonimowe uwierzytelnianie NTLM|  
|Użytkownik domeny|NTLM|NTLM|Kerberos|Kerberos|  
|Komputer domeny|NTLM|NTLM|Kerberos|Kerberos|  
  
 W każdym przypadku cztery typy kont obejmują:  
  
- Użytkownik lokalny: Profil użytkownika tylko dla komputera. Na przykład: `MachineName\Administrator` lub `MachineName\ProfileName`.  
  
- System lokalny: Wbudowanego systemu kont na komputerze, który nie jest przyłączony do domeny.  
  
- Użytkownik domeny: Konto użytkownika w domenie systemu Windows. Na przykład: `DomainName\ProfileName`.  
  
- Komputer domeny: Proces z tożsamością komputera uruchomioną na komputerze przyłączonym do domeny systemu Windows. Na przykład: `MachineName\Network Service`.  
  
> [!NOTE]
> Poświadczenie usługi jest przechwytywane, <xref:System.ServiceModel.ICommunicationObject.Open%2A> gdy wywoływana jest <xref:System.ServiceModel.ServiceHost> metoda klasy. Poświadczenie klienta jest odczytywane za każdym razem, gdy klient wysyła komunikat.  
  
## <a name="common-windows-authentication-problems"></a>Typowe problemy z uwierzytelnianiem systemu Windows  
 W tej sekcji omówiono niektóre typowe problemy z uwierzytelnianiem systemu Windows i możliwe środki zaradcze.  
  
### <a name="kerberos-protocol"></a>Protokół Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Problemy z nazwą SPN/UPN przy użyciu protokołu Kerberos  
 W przypadku korzystania z uwierzytelniania systemu Windows, gdy protokół Kerberos jest używany lub negocjowany przez interfejs SSPI, adres URL używany przez punkt końcowy klienta musi zawierać w pełni kwalifikowaną nazwę domeny hosta usługi w ramach adresu URL usługi. Przyjęto założenie, że konto, na którym jest uruchomiona usługa, ma dostęp do komputera (domyślnego) klucza głównej nazwy usługi (SPN), który jest tworzony podczas dodawania komputera do domeny Active Directory, co jest najczęściej wykonywane przez uruchomienie usługi w ramach Konto usługi sieciowej. Jeśli usługa nie ma dostępu do klucza nazwy SPN komputera, należy podać poprawną nazwę SPN lub głównej nazwy użytkownika (UPN) konta, pod którym uruchomiona jest usługa w tożsamości punktu końcowego klienta. Aby uzyskać więcej informacji na temat działania programu WCF z nazwami SPN i UPN, zobacz [tożsamość usługi i uwierzytelnianie](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 W scenariuszach równoważenia obciążenia, takich jak farmy sieci Web lub ogrody sieci Web, typową metodą jest zdefiniowanie unikatowego konta dla każdej aplikacji, przypisanie nazwy SPN do tego konta i upewnienie się, że wszystkie usługi aplikacji działają na tym koncie.  
  
 Aby uzyskać nazwę SPN konta usługi, musisz być administratorem domeny Active Directory. Aby uzyskać więcej informacji, zobacz [dodatek dotyczący protokołu Kerberos dla systemu Windows](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Protokół Kerberos Direct wymaga, aby usługa działała w ramach konta komputera domeny  
 Dzieje się tak, `ClientCredentialType` gdy właściwość jest ustawiona `Windows` na, <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> a właściwość jest ustawiona `false`na, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Aby rozwiązać ten sposób, uruchom usługę przy użyciu konta komputera domeny, takiego jak usługa sieciowa, na komputerze przyłączonym do domeny.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegowanie wymaga negocjowania poświadczeń  
 Aby użyć protokołu uwierzytelniania Kerberos z delegowaniem, należy zaimplementować protokół Kerberos za pomocą negocjacji poświadczeń (czasami nazywany "wieloetapowym" lub "wieloetapowym" Kerberos). W przypadku zaimplementowania uwierzytelniania przy użyciu protokołu Kerberos bez negocjowania poświadczeń (nazywanego czasem "pojedynczym zrzutem" lub "jednoetapowa" Kerberos) zostanie zgłoszony wyjątek.  
  
 Aby zaimplementować protokół Kerberos za pomocą negocjacji poświadczeń, wykonaj następujące czynności:  
  
1. Implementowanie delegowania <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> przez <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>ustawienie do.  
  
2. Wymagaj negocjacji interfejsu SSPI:  
  
    1. Jeśli używasz powiązań standardowych, ustaw `NegotiateServiceCredential` właściwość na. `true`  
  
    2. Jeśli używasz powiązań niestandardowych, ustaw `AuthenticationMode` atrybut `Security` elementu na `SspiNegotiated`.  
  
3. Wymagaj negocjacji interfejsu SSPI do korzystania z protokołu Kerberos przez niezezwalanie na korzystanie z uwierzytelniania NTLM:  
  
    1. Zrób to w kodzie, z następującą instrukcją:`ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2. Lub można to zrobić w pliku konfiguracji przez ustawienie `allowNtlm` atrybutu na. `false` Ten atrybut jest zawarty w [ \<> systemu Windows](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protokół NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Negocjowanie dostawcy SSP powraca do protokołu NTLM, ale uwierzytelnianie NTLM jest wyłączone  
 Właściwość jest ustawiona na `false`, co powoduje, że Windows Communication Foundation (WCF), aby najlepszym wysiłku zgłosić wyjątek, jeśli jest używany protokół NTLM. <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Należy pamiętać, że ustawienie tej `false` właściwości na nie zapobiega wysyłaniu poświadczeń NTLM za pośrednictwem sieci.  
  
 Poniżej przedstawiono sposób wyłączenia powrotu do protokołu NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Logowanie NTLM kończy się niepowodzeniem  
 Poświadczenia klienta nie są prawidłowe w usłudze. Sprawdź, czy nazwa użytkownika i hasło są poprawnie ustawione i odpowiadają kontu znanemu komputerowi, na którym uruchomiono usługę. Protokół NTLM używa określonych poświadczeń do logowania się do komputera usługi. Poświadczenia mogą być prawidłowe na komputerze, na którym jest uruchomiony klient programu, więc logowanie nie powiedzie się, jeśli poświadczenia na komputerze usługi nie są prawidłowe.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Występuje anonimowe logowanie NTLM, ale Logowanie anonimowe jest domyślnie wyłączone  
 Podczas tworzenia klienta <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość jest ustawiona na <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, jak pokazano w poniższym przykładzie, ale domyślnie serwer nie zezwala na Logowanie anonimowe. Dzieje się tak, ponieważ wartość <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> domyślna właściwości <xref:System.ServiceModel.Security.WindowsServiceCredential> klasy to `false`.  
  
 Poniższy kod klienta próbuje włączyć Logowanie anonimowe (należy pamiętać, że właściwość domyślna to `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Poniższy kod usługi zmienia wartość domyślną, aby umożliwić Logowanie anonimowe przez serwer.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Aby uzyskać więcej informacji na temat personifikacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Alternatywnie klient działa jako usługa systemu Windows przy użyciu wbudowanego systemu kont.  
  
### <a name="other-problems"></a>Inne problemy  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Poświadczenia klienta nie są ustawione prawidłowo  
 Uwierzytelnianie systemu Windows używa <xref:System.ServiceModel.Security.WindowsClientCredential> wystąpienia zwróconego <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> przez właściwość <xref:System.ServiceModel.ClientBase%601> klasy, a <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>nie elementu. Poniżej przedstawiono nieprawidłowy przykład.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Poniżej przedstawiono poprawność przykładu.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Interfejs SSPI jest niedostępny  
 Następujące systemy operacyjne nie obsługują uwierzytelniania systemu Windows, gdy jest używany jako serwer: [!INCLUDE[wxp](../../../../includes/wxp-md.md)]Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition i [!INCLUDE[wv](../../../../includes/wv-md.md)]wersje Home.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Opracowywanie i wdrażanie przy użyciu różnych tożsamości  
 Jeśli tworzysz aplikację na jednej maszynie i wdrażasz ją na innym serwerze i używasz innych typów kont do uwierzytelniania na każdej maszynie, może wystąpić inne zachowanie. Załóżmy na przykład, że tworzysz aplikację na komputerze z systemem Windows XP Pro przy użyciu `SSPI Negotiated` trybu uwierzytelniania. Jeśli używasz konta użytkownika lokalnego do uwierzytelniania za pomocą programu, zostanie użyty protokół NTLM. Po opracowaniu aplikacji należy wdrożyć usługę na komputerze z systemem Windows Server 2003, na którym działa w ramach konta domeny. W tym momencie klient nie będzie w stanie uwierzytelnić usługi, ponieważ będzie korzystać z protokołu Kerberos i kontrolera domeny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
