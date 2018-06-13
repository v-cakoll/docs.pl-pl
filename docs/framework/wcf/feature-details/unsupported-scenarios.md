---
title: Nieobsługiwane scenariusze
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 5cc4e65ce4f93a352b651203757a484a9d90a85d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507717"
---
# <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze
Windows Communication Foundation (WCF) z różnych powodów, nie obsługuje niektóre scenariusze zabezpieczeń. Na przykład [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition nie obsługuje protokoły uwierzytelniania SSPI lub protokołu Kerberos i w związku z tym WCF nie obsługuje uruchamiania usługi z uwierzytelnianiem systemu Windows na tej platformie. Innych mechanizmów uwierzytelniania, takich jak nazwy użytkownika i hasła i zintegrowane uwierzytelnianie HTTP i HTTPS są obsługiwane podczas uruchamiania usługi WCF w systemie Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Scenariusze personifikacji  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Personifikowanej tożsamości nie mogą przepływać wprowadzasz klientów wywołania asynchroniczne  
 Jeśli klient WCF wywołań asynchronicznych z usługą WCF za pomocą uwierzytelniania systemu Windows w ramach personifikacji, uwierzytelniania mogą wystąpić przy użyciu tożsamości procesu klienta zamiast personifikowanej tożsamości.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP i tokenu pliku Cookie bezpiecznym kontekście włączone  
 Usługi WCF nie obsługuje personifikacji i <xref:System.InvalidOperationException> jest generowany, gdy istnieją następujące warunki:  
  
-   System operacyjny jest [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Tryb uwierzytelniania powoduje tożsamości systemu Windows.  
  
-   <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute> ma ustawioną wartość <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
-   Utworzono token kontekstu zabezpieczeń oparte na stanie (SCT) (domyślnie tworzenie zostało wyłączone).  
  
 Oparte na stanie SCT można tworzyć tylko za pomocą niestandardowego powiązania. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpieczną sesję](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) W kodzie, token jest włączona, tworząc elementu powiązania zabezpieczeń (albo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> lub <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> — metoda i ustawienie `requireCancellation` parametr `false`. Parametr odwołuje się do buforowania SCT. Ustawienie wartości `false` włącza funkcję SCT oparte na stanie.  
  
 Alternatywnie w konfiguracji, token jest włączona, tworząc <`customBinding`>, następnie dodając <`security`> elementu i ustawienie `authenticationMode` atrybutu SecureConversation i `requireSecurityContextCancellation` atrybutu `true`.  
  
> [!NOTE]
>  Specyficznych powyższych wymagań. Na przykład <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> tworzy element powiązania, który powoduje tożsamości systemu Windows, ale nie wprowadza SCT. W związku z tym użytkownik może być używany z `Required` opcja [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Możliwe konflikt ASP.NET  
 Usługi WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jednocześnie włączyć lub wyłączyć personifikację. Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacja WCF hostuje konflikt mogą istnieć między usługi WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ustawienia konfiguracji. W przypadku konfliktu, ustawienie WCF ma pierwszeństwo, chyba że <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość jest ustawiona na <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, w którym to przypadku [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pierwszeństwo ma ustawienie personifikacji.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Ładunki zestaw może zakończyć się niepowodzeniem w ramach personifikacji  
 Jeśli spersonifikowanym kontekście nie ma praw dostępu do załadowania zestawu, a jeśli po raz pierwszy środowisko uruchomieniowe języka wspólnego (CLR) próbuje załadować zestawu dla tego elementu AppDomain, <xref:System.AppDomain> buforuje awarii. Niepowodzenie kolejnych prób załadować tego zestawu (lub zestawy), nawet po przywróceniu personifikacji, a nawet wtedy, gdy kontekst przywróconego ma prawa dostępu do ładowania zestawu. Jest to spowodowane CLR nie ponów próbę obciążenia po zmianie kontekstu użytkownika. Domeny aplikacji do odzyskiwania danych po awarii, należy ponownie.  
  
> [!NOTE]
>  Wartość domyślna dla <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> jest klasa <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. W większości przypadków kontekstu identyfikacji poziom personifikacji nie ma praw do załadowania dowolnych dodatkowych zestawów. Wartością domyślną jest więc jest to bardzo powszechne pod uwagę. Identyfikator poziomu personifikacji występuje także, gdy proces personifikacji nie ma `SeImpersonate` uprawnień. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegowanie wymaga negocjowania poświadczeń  
 Aby używać protokołu uwierzytelniania Kerberos z delegowania, musi implementować protokołu Kerberos z negocjowania poświadczeń (nazywane również wieloetapowego lub wieloetapowych protokołu Kerberos). Uwierzytelnianie Kerberos w przypadku zastosowania bez negocjowania poświadczeń (nazywane również jednorazowej lub jeden etap protokołu Kerberos), jest zwracany wyjątek. Aby uzyskać więcej informacji dotyczących sposobu wdrażania negocjowania poświadczeń, zobacz [Debugowanie błędów uwierzytelniania systemu Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Kryptografia  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>Algorytm SHA-256 jest obsługiwane tylko w przypadku użycia klucza symetrycznego  
 Usługi WCF obsługuje wiele algorytmów szyfrowania i podpisywania szyfrowanego tworzenia, które można określić przy użyciu pakietu algorytmów powiązania dostarczane przez system. Ze względów bezpieczeństwa WCF obsługuje algorytmy Secure Hash Algorithm (SHA) 2, w szczególności algorytmu SHA-256, służący do tworzenia skrótów skrótu podpisu. Ta wersja obsługuje algorytm SHA-256, tylko w przypadku użycia klucza symetrycznego, takie jak klucze Kerberos i których certyfikat X.509 nie jest używany do podpisywania wiadomości. Usługi WCF nie obsługuje podpisów RSA (używane w certyfikatach X.509) przy użyciu skrótu SHA-256 ze względu na Brak bieżącej obsługi RSA-SHA256 w [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Zgodne ze standardem FIPS skrótów algorytmu SHA-256, nie jest obsługiwane  
 Usługi WCF nie obsługuje wartości skrótu SHA-256 zgodne ze standardem FIPS, więc mechanizmów algorytmu, które korzystają z algorytmu SHA-256 nie są obsługiwane przez usługi WCF w systemach, w którym wymagany jest Użyj zgodnych algorytmów FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Zgodnych algorytmów FIPS może zakończyć się niepowodzeniem w przypadku modyfikacji rejestru  
 Można włączyć i wyłączyć przetwarzania standardami FIPS (Federal Information) - algorytmów za pomocą przystawki lokalnych zabezpieczeń ustawienia programu Microsoft Management Console (MMC) - w. Można także przejść ustawienie w rejestrze. Należy jednak pamiętać, że usługi WCF nie jest obsługiwana za pomocą rejestru, aby zresetować ustawienie. Jeśli wartość jest ustawiona na inny niż 1 lub 0, pomiędzy środowiska CLR i systemu operacyjnego mogą występować niespójne wyniki.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Ograniczenie szyfrowania AES zgodne ze standardem FIPS  
 Szyfrowanie AES zgodne ze standardem FIPS nie działa w dupleksowego wywołania zwrotnego w obszarze identyfikacji poziomu personifikacji.  
  
### <a name="cngksp-certificates"></a>CNG/KLUCZY certyfikatów  
 *Cryptography API: Next Generation (CNG)* długoterminowej zastępuje interfejsu CryptoAPI. Ten interfejs API jest dostępny w niezarządzanym kodzie [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] i nowszych wersjach systemu Windows.  
  
 .NET framework 4.6.1 i wcześniejsze wersje nie obsługują tych certyfikatów, ponieważ używają starszej wersji CryptoAPI do obsługi certyfikatów CNG/dostawcy magazynu KLUCZY. Korzystanie z tych certyfikatów z platformy .NET Framework 4.6.1 i wcześniejszych wersjach spowoduje, że wystąpił wyjątek.  
  
 Istnieją dwa sposoby, aby sprawdzić, czy certyfikat używa dostawcy magazynu KLUCZY:  
  
-   Czy `p/invoke` z `CertGetCertificateContextProperty`i sprawdzić `dwProvType` w zwróconym `CertGetCertificateContextProperty`.  
  
-   Użyj `certutil` polecenie w wierszu polecenia na potrzeby zapytań certyfikatów. Aby uzyskać więcej informacji, zobacz [zadania narzędzia Certutil dotyczące rozwiązywania problemów z certyfikatami](http://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Komunikat zabezpieczeń kończy się niepowodzeniem użycie personifikacji aplikacji ASP.NET i zgodności z platformą ASP.NET jest wymagana  
 Usługi WCF nie obsługuje następujących kombinacji ustawień, ponieważ ich może uniemożliwić uwierzytelnienie klienta występowaniu:  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Personifikacja jest włączona. Odbywa się w pliku Web.config przez ustawienie `impersonate` atrybut <`identity`> elementu `true`.  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Tryb zgodności jest włączony, ustawiając `aspNetCompatibilityEnabled` atrybutu [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) do `true`.  
  
-   Zabezpieczenia komunikatów tryb jest używany.  
  
 Obejście jest wyłączyć [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] w trybie zgodności. Lub, jeśli [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] wymagany jest w trybie zgodności, wyłącz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] personifikacji funkcji i zamiast tego należy używać personifikacji dostarczonych do usługi WCF. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Błąd literału adres IPv6  
 Żądania zabezpieczeń zakończyć się niepowodzeniem, gdy klient i usługa są na tym samym komputerze, i literału adresy IPv6 są używane przez usługę.  
  
 Literał IPv6 rozwiązuje pracy, jeśli usługa i klient znajdują się na różnych komputerach.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Błędy pobierania WSDL z zaufaniem federacyjnym  
 Usługi WCF wymaga dokładnie jeden dokument WSDL dla każdego węzła w łańcuchu zaufania federacji. Nie można więc skonfigurować pętlę w przypadku określania punktów końcowych. Jeden sposób, w którym mogą wystąpić pętle używa pobieranie WSDL łańcuchów zaufania federacyjnego z co najmniej dwóch łączy, w tym samym dokumencie WSDL. Typowy scenariusz, który może utworzyć ten problem jest usługi federacyjnej, gdzie serwer tokenu zabezpieczeń i usługi znajdują się wewnątrz tego samego elementu ServiceHost.  
  
 Przykładem takiej sytuacji jest usługi za pomocą następujących trzech adresy punktów końcowych:  
  
-   http://localhost/CalculatorService/service (usługa)  
  
-   http://localhost/CalculatorService/issue_ticket (STS)  
  
-   http://localhost/CalculatorService/mex (punkt końcowy metadanych)  
  
 To zgłasza wyjątek.  
  
 Możesz wprowadzić w tym scenariuszu działać przez umieszczenie `issue_ticket` punktu końcowego w innym miejscu.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Atrybuty importu WSDL mogą być utracone  
 WCF utraci Śledź atrybutów na `<wst:Claims>` element `RST` szablonu podczas importu WSDL. Jeśli określisz dzieje podczas importu WSDL `<Claims>` bezpośrednio w `WSFederationHttpBinding.Security.Message.TokenRequestParameters` lub `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` bezpośrednio zamiast kolekcji typów oświadczeń.  Ponieważ importu utraci atrybuty, powiązania nie Rundy prawidłowo za pośrednictwem WSDL i dlatego jest nieprawidłowy po stronie klienta.  
  
 Będzie można zmodyfikować powiązanie bezpośrednio na komputerze klienckim po wykonaniu importu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
