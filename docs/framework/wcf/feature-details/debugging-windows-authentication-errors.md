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
ms.openlocfilehash: d9226324b69e5c27738abb35bb155a43964b9127
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-windows-authentication-errors"></a>Debugowanie błędów uwierzytelniania systemu Windows
Korzystając z uwierzytelniania systemu Windows jako mechanizm zabezpieczeń, interfejsu dostawcy obsługi zabezpieczeń (SSPI) obsługuje procesów zabezpieczeń. W przypadku wystąpienia błędów zabezpieczeń w warstwie SSPI, są one udostępniane przez Windows Communication Foundation (WCF). Ten temat zawiera framework i zestawu pytania, aby pomóc w zdiagnozowaniu błędów.  
  
 Omówienie protokołu Kerberos, zobacz [protokołu Kerberos](http://go.microsoft.com/fwlink/?LinkID=86946); w przypadku zobacz omówienie interfejsu SSPI, [SSPI](http://go.microsoft.com/fwlink/?LinkId=88941).  
  
 W przypadku uwierzytelniania systemu Windows, zazwyczaj używa WCF *Negotiate* Obsługa dostawca zabezpieczeń (SSP), który przeprowadza uwierzytelnianie wzajemne Kerberos między klientem a usługą. Jeśli protokół Kerberos nie jest dostępny, domyślnie WCF powraca do programu NT LAN Manager (NTLM). Można jednak skonfigurować WCF do korzystania z protokołu Kerberos (i Zgłoś wyjątek, jeśli protokół Kerberos nie jest dostępna). Można również skonfigurować usługi WCF do użycia formularze ograniczone protokołu Kerberos.  
  
## <a name="debugging-methodology"></a>Metodologia debugowania  
 Podstawowa metoda wygląda następująco:  
  
1.  Określ, czy używasz uwierzytelniania systemu Windows. Jeśli korzystasz z innego systemu, w tym temacie nie ma zastosowania.  
  
2.  Jeśli masz pewność, że używasz uwierzytelniania systemu Windows, należy określić, czy konfiguracji WCF używa protokołu Kerberos, bezpośrednio lub Negotiate.  
  
3.  Po określeniu, czy konfiguracja jest przy użyciu protokołu Kerberos lub NTLM, można zrozumieć, komunikaty o błędach w poprawny kontekst.  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a>Dostępność protokołu Kerberos i NTLM  
 Dostawca obsługi zabezpieczeń Kerberos wymaga kontrolera domeny do działania jako centrum dystrybucji kluczy (KDC) protokołu Kerberos. Protokół Kerberos jest dostępne tylko wtedy, gdy klient i usługa są przy użyciu tożsamości domeny. W innych kombinacji kont NTLM jest używany, zgodnie z opisem w poniższej tabeli.  
  
 Nagłówki tabeli przedstawiono typy kont używane przez serwer. W lewej kolumnie pokazany typów kont używanych przez klienta.  
  
||Użytkownik lokalny|System lokalny|Użytkownik domeny|Komputerze domeny|  
|-|----------------|------------------|-----------------|--------------------|  
|Użytkownik lokalny|NTLM|NTLM|NTLM|NTLM|  
|System lokalny|Anonimowe NTLM|Anonimowe NTLM|Anonimowe NTLM|Anonimowe NTLM|  
|Użytkownik domeny|NTLM|NTLM|Kerberos|Kerberos|  
|Komputerze domeny|NTLM|NTLM|Kerberos|Kerberos|  
  
 W szczególności cztery typy kont obejmują:  
  
-   Użytkownika lokalnego: Profil użytkownika tylko do komputera. Na przykład: `MachineName\Administrator` lub `MachineName\ProfileName`.  
  
-   System lokalny: Wbudowane konto systemowe na komputerze, na którym nie jest przyłączony do domeny.  
  
-   Użytkownik domeny: Konto użytkownika w domenie systemu Windows. Na przykład: `DomainName\ProfileName`.  
  
-   Komputer do domeny: Proces z tożsamością maszyny uruchomiony na komputer przyłączony do domeny systemu Windows. Na przykład: `MachineName\Network Service`.  
  
> [!NOTE]
>  Poświadczenie usługi są przechwytywane podczas <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody <xref:System.ServiceModel.ServiceHost> nosi nazwę klasy. Poświadczenie klienta jest do odczytu zawsze, gdy klient wysyła wiadomość.  
  
## <a name="common-windows-authentication-problems"></a>Typowe problemy z uwierzytelnianiem systemu Windows  
 W tej sekcji opisano niektóre typowe problemy z uwierzytelnianiem systemu Windows i możliwości.  
  
### <a name="kerberos-protocol"></a>Protokół Kerberos  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a>Nazwa SPN/nazwa UPN problemów przy użyciu protokołu Kerberos  
 Korzystając z uwierzytelniania systemu Windows i protokołu Kerberos, protokół jest używany lub wynegocjowanym przez interfejs SSPI, adres URL punktu końcowego klienta używa musi zawierać w pełni kwalifikowana nazwa domeny hosta usługi wewnątrz adres URL usługi. Przy założeniu, że konto, na którym uruchomiono usługę ma prawa dostępu do klucza głównej nazwy (usługi SPN) usługi maszyny (ustawienie domyślne), który jest tworzony po dodaniu komputera do domeny usługi Active Directory, najczęściej jest to zrobić, uruchamiając usługi w Konto Usługa sieciowa. Jeśli usługa nie ma dostępu do klucza SPN komputera, należy podać poprawną nazwę SPN lub użytkownika nazwę główną (UPN) konta, pod którym usługa jest uruchomiona w tożsamości punktu końcowego klienta. Aby uzyskać więcej informacji na temat działania usługi WCF z nazw SPN i UPN, zobacz [uwierzytelnianie i tożsamość usługi](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 W programie Równoważenie obciążenia scenariusze, takie jak farmy serwerów sieci Web lub ogrodach sieci Web popularną praktyką jest zdefiniuj unikatowe konto dla poszczególnych aplikacji, Przypisz nazwę SPN dla tego konta i upewnij się, że wszystkie usługi aplikacji uruchomione na tym koncie.  
  
 Aby uzyskać nazwę SPN konta usługi, musisz być administratorem domeny usługi Active Directory. Aby uzyskać więcej informacji, zobacz [Kerberos techniczne dodatku dla systemu Windows](http://go.microsoft.com/fwlink/?LinkID=88330).  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a>Protokół Kerberos Direct wymaga usługi do uruchomienia konta komputera do domeny  
 Dzieje się tak, gdy `ClientCredentialType` właściwość jest ustawiona na `Windows` i <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwość jest ustawiona na `false`, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 Aby rozwiązać, uruchom tę usługę, używając konta domeny komputera, na przykład usługi sieciowej, w domenie przyłączone do komputera.  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegowanie wymaga negocjowania poświadczeń  
 Aby używać protokołu uwierzytelniania Kerberos z delegowania, musi implementować protokołu Kerberos z negocjowania poświadczeń (nazywane czasem "wieloetapowego" lub "wieloetapowych" Kerberos). Uwierzytelnianie Kerberos w przypadku zastosowania bez negocjowania poświadczeń (nazywane czasem "jednorazowej" lub "jeden etap" Kerberos), zostanie wygenerowany wyjątek.  
  
 Do implementowania protokołu Kerberos z negocjowania poświadczeń, wykonaj następujące czynności:  
  
1.  Implementowanie delegowania przez ustawienie <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> do <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.  
  
2.  Wymagaj negocjowanie interfejsu SSPI:  
  
    1.  Jeśli używasz standardowego powiązania ustawić `NegotiateServiceCredential` właściwości `true`.  
  
    2.  Jeśli używasz niestandardowego powiązania, ustaw `AuthenticationMode` atrybutu `Security` elementu `SspiNegotiated`.  
  
3.  Wymagaj negocjowanie interfejsu SSPI, aby używać protokołu Kerberos, zezwalając na korzystanie z uwierzytelniania NTLM:  
  
    1.  Wykonaj następujące czynności w kodzie, z następujących instrukcji: `ChannelFactory.Credentials.Windows.AllowNtlm = false`  
  
    2.  Lub możesz zrobić to w pliku konfiguracji przez ustawienie `allowNtlm` atrybutu `false`. Ten atrybut jest zawarta w [ \<windows >](../../../../docs/framework/configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).  
  
### <a name="ntlm-protocol"></a>Protokół NTLM  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a>Negocjowania SSP powróci do uwierzytelniania NTLM, ale uwierzytelnianie NTLM jest wyłączone.  
 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> Właściwość jest ustawiona na `false`, co powoduje, że Windows Communication Foundation (WCF) aby optymalnych zostać zgłoszony wyjątek, jeśli używane jest uwierzytelnianie NTLM. Należy pamiętać, że ustawienie tej właściwości na `false` może uniemożliwia poświadczeń NTLM są przesyłane przez sieć.  
  
 Poniżej przedstawiono sposób wyłączania powrotu do uwierzytelniania NTLM.  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a>Niepowodzenia logowania NTLM  
 Poświadczenia klienta nie są prawidłowe w usłudze. Sprawdź, czy nazwa użytkownika i hasło są poprawnie ustawione i odpowiadać na konto, które jest znany na komputerze, na którym jest uruchomiona usługa. NTLM korzysta z określonych poświadczeń do logowania się do komputera usługi. Poświadczenia mogą być prawidłowy na komputerze, na którym działa klient, to logowanie zakończy się niepowodzeniem, jeśli poświadczenia nie są prawidłowe dla komputera usługi.  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a>Logowania z anonimowych NTLM występuje, ale anonimowego logowania są domyślnie wyłączone  
 Podczas tworzenia klienta, <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość jest ustawiona na <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, jak pokazano w poniższym przykładzie, ale domyślnie serwer nie zezwala na logowanie anonimowe. Dzieje się tak, ponieważ domyślna wartość <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> właściwość <xref:System.ServiceModel.Security.WindowsServiceCredential> jest klasa `false`.  
  
 Poniższy kod klienta próbuje włączyć anonimowego logowania (należy pamiętać, że jest właściwością domyślną `Identification`).  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 Poniższy kod usługi zmienia domyślne można włączyć anonimowego logowania przez serwer.  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 Aby uzyskać więcej informacji o personifikacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
 Alternatywnie klient jest uruchomiony jako usługa systemu Windows przy użyciu wbudowanego konta SYSTEM.  
  
### <a name="other-problems"></a>Inne problemy  
  
#### <a name="client-credentials-are-not-set-correctly"></a>Poświadczenia klienta nie są poprawnie ustawione.  
 Uwierzytelnianie systemu Windows przy użyciu <xref:System.ServiceModel.Security.WindowsClientCredential> zwrócone przez wystąpienie <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> właściwość <xref:System.ServiceModel.ClientBase%601> klasy nie <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>. Poniżej przedstawiono przykład nieprawidłowy.  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 Poniżej przedstawiono przykład poprawnego.  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a>Interfejs SSPI nie jest dostępna  
 Następujące systemy operacyjne nie obsługują uwierzytelnianie systemu Windows, gdy jest używany jako serwer: [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Media Center Edition i [!INCLUDE[wv](../../../../includes/wv-md.md)]Home Edition.  
  
#### <a name="developing-and-deploying-with-different-identities"></a>Tworzenie i wdrażanie z różnych tożsamości  
 Jeśli aplikacja na komputerze i wdrażanie na innym i używają różnych typów kont do uwierzytelniania na każdej maszynie, możesz napotkać inaczej. Na przykład, załóżmy, że opracowywanie aplikacji przy użyciu systemu Windows XP Pro maszyny `SSPI Negotiated` tryb uwierzytelniania. Jeśli używasz konta użytkownika lokalnego uwierzytelniania za pomocą protokołu NTLM będzie używany. Po aplikacji do opracowania, możesz wdrożyć usługę do maszyny z systemem Windows Server 2003, którym został uruchomiony w ramach konta domeny. W tym momencie klienta nie będzie do uwierzytelniania usługi, ponieważ będą używać protokołu Kerberos i kontrolera domeny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.Security.WindowsServiceCredential>  
 <xref:System.ServiceModel.Security.WindowsClientCredential>  
 <xref:System.ServiceModel.ClientBase%601>  
 [Delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
