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
ms.openlocfilehash: 28c70ca860083808c93fa58b498e22ea4e4ca6cb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048052"
---
# <a name="debugging-windows-authentication-errors"></a>Debugowanie błędów uwierzytelniania systemu Windows
Korzystając z uwierzytelniania Windows jako mechanizm bezpieczeństwa, interfejs dostawcy obsługi zabezpieczeń (SSPI) obsługuje zabezpieczenia procesów. Po wystąpieniu błędów zabezpieczeń w warstwie interfejsu SSPI, są one udostępniane przez Windows Communication Foundation (WCF). Ten temat zawiera framework i zestaw pytań, aby łatwiej diagnozować błędy.  
  
 Omówienie protokołu Kerberos, zobacz [protokołu Kerberos](https://go.microsoft.com/fwlink/?LinkID=86946); zobacz omówienie interfejsu SSPI, [SSPI](https://go.microsoft.com/fwlink/?LinkId=88941).  
  
 W przypadku uwierzytelniania Windows WCF zwykle korzysta z *Negotiate* Dostawca obsługi zabezpieczeń (SSP), który wykonuje Kerberos uwierzytelnianie wzajemne między klientem a usługą. Jeśli protokół Kerberos nie jest dostępna, domyślnie WCF powraca do programu NT LAN Manager (NTLM). Można jednak skonfigurować WCF do korzystania z protokołu Kerberos (i zgłosić wyjątek, jeśli protokół Kerberos nie jest dostępna). Można również skonfigurować usługi WCF na użycie metod ograniczone protokołu Kerberos.  
  
## <a name="debugging-methodology"></a>Metodologia debugowania  
 Metoda podstawowa jest w następujący sposób:  
  
1. Ustal, czy korzystasz z uwierzytelniania Windows. Jeśli używasz innego systemu w tym temacie nie ma zastosowania.  
  
2. Jeśli masz pewność, że używasz uwierzytelniania Windows, należy określić, czy konfiguracji usługi WCF używa protokołu Kerberos, bezpośrednio lub Negotiate.  
  
3. Po określeniu, czy konfiguracja używa protokołu Kerberos lub NTLM, można zrozumieć, komunikaty o błędach w odpowiednim kontekście.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Dostępność protokołu Kerberos i NTLM  
 Dostawca obsługi zabezpieczeń Kerberos wymaga kontrolera domeny do działania jako centrum dystrybucji kluczy (KDC) protokołu Kerberos. Protokół Kerberos jest dostępna tylko wtedy, gdy klient i usługa są przy użyciu tożsamości domeny. W przypadku innych kombinacji konta NTLM jest używana zgodnie z opisem w poniższej tabeli.  
  
 Nagłówki tabeli Pokaż typy możliwe konto używane przez serwer. Kolumna po lewej stronie zawiera typy kont używanych przez klienta.  
  
||Użytkownik lokalny|Local System|Domena użytkownik|Maszyny do domeny|  
|-|----------------|------------------|-----------------|--------------------|  
|Użytkownik lokalny|NTLM|NTLM|NTLM|NTLM|  
|Local System|Anonymous NTLM|Anonymous NTLM|Anonymous NTLM|Anonymous NTLM|  
|Domena użytkownik|NTLM|NTLM|Kerberos|Kerberos|  
|Maszyny do domeny|NTLM|NTLM|Kerberos|Kerberos|  
  
 W szczególności cztery typy kont obejmują:  
  
- Użytkownik lokalny: Profil użytkownika tylko do maszyny. Na przykład: `MachineName\Administrator` lub `MachineName\ProfileName`.  
  
- Local System: Wbudowane konto SYSTEM na komputerze, który nie jest przyłączony do domeny.  
  
- Użytkownik domeny: Konto użytkownika domeny Windows. Na przykład: `DomainName\ProfileName`.  
  
- Komputer do domeny: Proces tożsamość komputera z uruchomioną na maszynie jest przyłączony do domeny Windows. Na przykład: `MachineName\Network Service`.  
  
> [!NOTE]
>  Poświadczenia usługi są przechwytywane podczas <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody <xref:System.ServiceModel.ServiceHost> nosi nazwę klasy. Poświadczeń klienta jest do odczytu zawsze, gdy klient wysyła komunikat.  
  
## <a name="common-windows-authentication-problems"></a>Typowe problemy z uwierzytelnianiem Windows  
 W tej sekcji omówiono niektóre typowe problemy z uwierzytelnianiem Windows i tymczasowe.  
  
### <a name="kerberos-protocol"></a>Protokół Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Główna nazwa usługi/nazwy UPN problemów przy użyciu protokołu Kerberos  
 Korzystając z uwierzytelniania Windows i protokołu Kerberos, protokół jest używany lub wynegocjowanym przez interfejs SSPI, adres URL punktu końcowego klienta używa musi zawierać w pełni kwalifikowaną nazwę domeny hosta usługi wewnątrz adres URL usługi. Założono, że konto, na którym uruchomiono usługę ma dostęp do klucza głównej nazwy (usługi SPN) usługi maszyny (ustawienie domyślne), który jest tworzony po dodaniu komputera do domeny usługi Active Directory, co zwykle odbywa się przez uruchomienie usługi w obszarze Konto Usługa sieciowa. Jeśli usługa nie ma dostępu do klucza nazwy SPN maszyny, musisz podać poprawną SPN lub użytkownika głównej nazwy (UPN) konta, w którym usługa jest uruchomiona w tożsamości punktu końcowego klienta. Aby uzyskać więcej informacji na temat współdziałania usługi WCF z nazwy SPN i UPN, zobacz [uwierzytelnianie i tożsamość usług](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 W programie Równoważenie obciążenia scenariusze, takie jak farmy serwerów sieci Web lub ogrodach sieci Web powszechną praktyką jest definiowanie unikatowe konto dla każdej aplikacji, przypisywanie nazwy SPN do tego konta i upewnij się, że wszystkie usługi aplikacji są uruchamiane w ramach tego konta.  
  
 Aby uzyskać nazwę SPN dla konta usługi, musisz mieć uprawnienia administratora domeny usługi Active Directory. Aby uzyskać więcej informacji, zobacz [Kerberos technicznego dodatku dla Windows](https://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Protokół Kerberos Direct wymaga usługi do uruchomienia w ramach konta komputera do domeny  
 Ten problem wystąpi podczas `ClientCredentialType` właściwość jest ustawiona na `Windows` i <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwość jest ustawiona na `false`, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Aby rozwiązać problem, uruchom usługę przy użyciu konta komputera do domeny, takie jak Usługa sieciowa, w domenie przyłączony komputer.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegowanie wymaga negocjowania poświadczeń  
 Aby używać protokołu uwierzytelniania Kerberos z delegowania, musi implementować protokołu Kerberos za pomocą negocjowania poświadczeń (czasami nazywany "wielu gałęzi" lub "wieloetapowego" protokołu Kerberos). W przypadku zaimplementowania uwierzytelniania Kerberos bez negocjowania poświadczeń (czasami nazywany "jednorazowej" lub "pojedynczej gałęzi" protokołu Kerberos), zostanie zgłoszony wyjątek.  
  
 Aby zaimplementować protokół Kerberos za pomocą negocjowania poświadczeń, wykonaj następujące czynności:  
  
1. Implementowanie delegowanie, ustawiając <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> do <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2. Wymagaj negocjacji interfejsu SSPI:  
  
    1. Jeśli używasz standardowego powiązania zestawu `NegotiateServiceCredential` właściwość `true`.  
  
    2. Jeśli używasz niestandardowego powiązania, ustaw `AuthenticationMode` atrybutu `Security` elementu `SspiNegotiated`.  
  
3. Wymagaj negocjacji interfejsu SSPI do używania protokołu Kerberos, nie można przydzielać korzystanie z uwierzytelniania NTLM:  
  
    1. Wykonaj następujące czynności w kodzie za pomocą następującej instrukcji: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2. Lub możesz to zrobić w pliku konfiguracji, ustawienia `allowNtlm` atrybutu `false`. Ten atrybut jest zawarty w [ \<systemu windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protokół NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Negocjowania SSP powróci do uwierzytelniania NTLM, ale uwierzytelnianie NTLM zostało wyłączone  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Właściwość jest ustawiona na `false`, co powoduje, że Windows Communication Foundation (WCF) umożliwiają staranności do zgłoszenia wyjątku, jeśli używane jest uwierzytelnianie NTLM. Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.  
  
 Poniżej przedstawiono sposób wyłączania powrót do uwierzytelniania NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Niepowodzenie logowania NTLM  
 Poświadczenia klienta są nieprawidłowe w usłudze. Upewnij się, że nazwa użytkownika i hasło są poprawnie ustawione i odnoszą się do konta które jest znana na komputerze, na którym jest uruchomiona usługa. NTLM korzysta z określonych poświadczeń do logowania się komputerze usługi. Poświadczenia mogą być prawidłowe na komputerze, na którym działa klient, to logowanie zakończy się niepowodzeniem, jeśli poświadczenia nie są prawidłowe dla komputera usługi.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Logowanie anonimowe NTLM występuje, ale anonimowego logowania są domyślnie wyłączone  
 Podczas tworzenia klienta <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość jest ustawiona na <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, jak pokazano w poniższym przykładzie, ale domyślnie serwer nie zezwala na logowanie anonimowe. Dzieje się tak dlatego wartość domyślną <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> właściwość <xref:System.ServiceModel.Security.WindowsServiceCredential> klasa jest `false`.  
  
 Poniższy kod klienta spróbuje włączyć logowanie anonimowe (należy zauważyć, że właściwość default `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Poniższy kod usługi zmienia domyślne, aby włączyć logowanie anonimowe przez serwer.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Aby uzyskać więcej informacji na temat personifikacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Alternatywnie klient jest uruchomiony jako usługa Windows przy użyciu wbudowanego konta SYSTEM.  
  
### <a name="other-problems"></a>Inne problemy  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Poświadczenia klienta nie zostały poprawnie skonfigurowane.  
 Korzysta z uwierzytelniania Windows <xref:System.ServiceModel.Security.WindowsClientCredential> wystąpienie zwrócone przez <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy nie <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Poniżej przedstawiono przykład nieprawidłowy.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Na poniższym obrazie przedstawiono przykład poprawnego.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Interfejs SSPI nie jest dostępna  
 Następujące systemy operacyjne nie obsługują uwierzytelniania Windows, gdy jest używana jako serwer: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition, i [!INCLUDE[wv](../../../../includes/wv-md.md)]Home Edition.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Tworzenie i wdrażanie przy użyciu różnych tożsamości  
 Jeśli tworzenia aplikacji na jednym komputerze wdrożeniu w innym, używają różnych typów kont do uwierzytelniania na każdej maszynie, mogą występować inne zachowanie. Załóżmy, że tworzenie aplikacji przy użyciu Windows XP Pro maszyny `SSPI Negotiated` tryb uwierzytelniania. Jeśli używasz konta użytkownika lokalnego do uwierzytelniania przy użyciu protokołu NTLM będą używane. Gdy aplikacja jest opracowana, możesz wdrożyć usługę do maszyny systemu Windows Server 2003, w którym został uruchomiony w ramach konta domeny. W tym momencie klient nie będzie mógł uwierzytelnić usługi, ponieważ będą używać protokołu Kerberos i kontrolerem domeny.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
