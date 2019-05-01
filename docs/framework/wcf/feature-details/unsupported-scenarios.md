---
title: Nieobsługiwane scenariusze
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 12012f3e0c0c3b0d10c5faebfb2de881f5de3917
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050756"
---
# <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze
Z różnych powodów Windows Communication Foundation (WCF) nie obsługuje niektóre scenariusze zabezpieczeń. Na przykład [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition nie zawiera implementacji protokołów uwierzytelniania SSPI lub protokołu Kerberos i w związku z tym WCF nie obsługuje uruchamiania usługi za pomocą uwierzytelniania Windows na tej platformie. Inne mechanizmy uwierzytelniania, takich jak nazwy użytkownika/hasła i zintegrowane uwierzytelnianie HTTP/HTTPS są obsługiwane podczas uruchamiania usługi WCF w obszarze Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Scenariusze personifikacji  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Personifikowanej tożsamości nie może być przepływu, gdy klienci wykonywanie wywołań asynchronicznych  
 Po klient WCF wywołań asynchronicznych do usługi WCF, za pomocą uwierzytelniania Windows w ramach personifikacji, uwierzytelnianie może wystąpić przy użyciu tożsamości procesu klienta zamiast personifikowanej tożsamości.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP i tokenu pliku Cookie bezpiecznym kontekście włączone  
 Usługi WCF nie obsługuje personifikacji i <xref:System.InvalidOperationException> jest zgłaszany, gdy następujące warunki:  
  
- System operacyjny jest [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Tryb uwierzytelniania powoduje tożsamości Windows.  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> Właściwość <xref:System.ServiceModel.OperationBehaviorAttribute> ustawiono <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
- Zostanie utworzony token kontekstu zabezpieczeń oparte na stanie (SCT) (domyślnie jest wyłączona tworzenia).  
  
 Oparte na stanie SCT można tworzyć tylko za pomocą niestandardowego powiązania. Aby uzyskać więcej informacji, zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).) W kodzie, token jest włączona, tworząc elementu powiązania zabezpieczeń (albo <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>) przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> lub <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> metody i ustawienie `requireCancellation` parametr `false`. Parametr odnosi się do buforowania SCT. Ustawienie wartości `false` włącza funkcję SCT na podstawie ich stanu.  
  
 Alternatywnie w konfiguracji, token jest włączona, tworząc <`customBinding`>, następnie dodając <`security`> elementu, a ustawienie `authenticationMode` atrybutu do mechanizmu SecureConversation i `requireSecurityContextCancellation` atrybutu `true`.  
  
> [!NOTE]
>  Poprzedni wymagania są określone. Na przykład <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> tworzy element powiązania, który powoduje tożsamości Windows, ale nie można ustalić SCT. W związku z tym, można użyć z `Required` opcja [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Możliwych konfliktów platformy ASP.NET  
 WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] jednocześnie włączyć lub wyłączyć personifikację. Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacja WCF hostuje konflikt mogą istnieć między WCF i [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ustawień konfiguracji. Jeśli konflikt, ustawienia usługi WCF, pierwszeństwo, chyba że <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość jest ustawiona na <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, w którym to przypadku [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pierwszeństwo ma ustawienie personifikacji.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Załadowań zestawów może zakończyć się niepowodzeniem w ramach personifikacji  
 Jeśli spersonifikowanym kontekście nie ma praw dostępu do załadowania zestawu, a jeśli po raz pierwszy środowisko uruchomieniowe języka wspólnego (CLR) próbuje załadować zestawu dla tego elementu AppDomain, <xref:System.AppDomain> buforuje awarii. Kolejne można załadować tego zestawu (lub zespoły) zakończy się niepowodzeniem, nawet po zakończeniu przywrócenie personifikacji, a nawet wtedy, gdy przywróconym kontekst ma wystarczające uprawnienia dostępu do załadowania zestawu. Jest to spowodowane CLR nie będzie ponownie podejmował prób obciążenia po zmianie kontekstu użytkownika. Należy ponownie uruchomić domeny aplikacji, aby dokonać odzyskiwania po awarii.  
  
> [!NOTE]
>  Wartością domyślną dla <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> właściwość <xref:System.ServiceModel.Security.WindowsClientCredential> klasa jest <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. W większości przypadków kontekstu identyfikacji poziom personifikacji nie ma uprawnień do załadowania dowolnych dodatkowych zestawów. Jest to wartość domyślna, więc jest to często zdarza się zapoznać. Identyfikacja poziom personifikacji występuje personifikacji proces nie ma `SeImpersonate` uprawnień. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegowanie wymaga negocjowania poświadczeń  
 Aby używać protokołu uwierzytelniania Kerberos z delegowania, musi implementować protokołu Kerberos za pomocą negocjowania poświadczeń (czasami nazywany wielu gałęzi lub wieloma krokami protokołu Kerberos). W przypadku zaimplementowania uwierzytelniania Kerberos bez negocjowania poświadczeń (czasami nazywany jednorazowej lub pojedynczej gałęzi protokołu Kerberos), wyjątek jest generowany. Aby uzyskać więcej informacji na temat implementacji negocjowania poświadczeń, zobacz [Debugowanie błędów uwierzytelniania Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Kryptografia  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>Algorytm SHA-256 jest obsługiwane tylko w przypadku użycia klucza symetrycznego  
 Usługi WCF obsługuje wiele różnych algorytmów szyfrowania i podpisywania szyfrowanego tworzenia określonych przez użytkownika za pomocą pakiet algorytmów w powiązania dostarczane przez system. Ze względów bezpieczeństwa WCF obsługuje algorytmy Secure Hash Algorithm (SHA) 2, w szczególności algorytmu SHA-256, tworzenia skrótów skrótu podpisu. Ta wersja obsługuje algorytm SHA-256, tylko w przypadku użycia klucza symetrycznego, takie jak klucze Kerberos i gdzie certyfikat X.509 nie jest używany do podpisywania wiadomości. Usługi WCF nie obsługuje podpisów RSA (używana w certyfikatach X.509) za pomocą wyznaczania wartości skrótu SHA-256, ze względu na Brak bieżącej obsługi dla algorytm RSA-SHA256 w [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Zgodne ze standardem FIPS skróty SHA-256, nie jest obsługiwane  
 Usługi WCF nie obsługuje skróty SHA-256 zgodne ze standardem FIPS, więc algorytm zestawów, korzystających z algorytmu SHA-256 nie są obsługiwane przez architekturę WCF w systemach, w których wymagane jest Użyj zgodnych algorytmów FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Zgodne ze standardem FIPS, algorytmów może zakończyć się niepowodzeniem w przypadku modyfikacji rejestru  
 Można włączyć i wyłączyć przetwarzania standardów FIPS (Federal Information) - algorytmów zgodnych z za pomocą przystawki usługi lokalne zabezpieczenia ustawienia programu Microsoft Management Console (MMC) - w. Można także przejść ustawienie w rejestrze. Należy jednak pamiętać, że usługi WCF nie obsługuje za pomocą rejestru, aby zresetować ustawienia. Jeśli wartość jest równa nic innego niż 1 lub 0, pomiędzy środowiska CLR i systemu operacyjnego mogą występować niespójne wyniki.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS-Compliant AES Encryption Limitation  
 Szyfrowanie AES zgodne ze standardem FIPS nie działa w dupleksowego wywołania zwrotnego w obszarze identyfikator poziomu personifikacji.  
  
### <a name="cngksp-certificates"></a>Certyfikatów CNG/dostawcy magazynu KLUCZY  
 *Cryptography API: Next Generation (CNG)* długoterminowe zastępuje interfejsu CryptoAPI. Ten interfejs API jest dostępny w niezarządzanym kodzie na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)] i nowsze wersje Windows.  
  
 Program .NET framework 4.6.1 i starsze wersje nie obsługują tych certyfikatów ponieważ używają one starszego interfejsu CryptoAPI do obsługi certyfikatów CNG/dostawcy magazynu KLUCZY. Korzystanie z tych certyfikatów przy użyciu platformy .NET Framework 4.6.1 i wcześniejszych wersji spowoduje, że wyjątek.  
  
 Istnieją dwa sposoby, aby sprawdzić, czy certyfikatu używa dostawcy magazynu KLUCZY:  
  
- Czy `p/invoke` z `CertGetCertificateContextProperty`i sprawdzić `dwProvType` na zwracanego `CertGetCertificateContextProperty`.  
  
- Użyj `certutil` polecenia z wiersza polecenia do wykonywania zapytań certyfikatów. Aby uzyskać więcej informacji, zobacz [zadania narzędzia Certutil dotyczące rozwiązywania problemów z certyfikatami](https://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Komunikat zabezpieczeń kończy się niepowodzeniem jeśli wymagane jest korzystanie z personifikacji aplikacji ASP.NET i zgodność platformy ASP.NET  
 Usługi WCF nie obsługuje następujących kombinacji ustawień, ponieważ mogą również uniemożliwiać uwierzytelnianie klienta występowaniu:  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Personifikacja jest włączona. Odbywa się w pliku Web.config, ustawiając `impersonate` atrybut <`identity`> elementu `true`.  
  
- [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Tryb zgodności jest włączony, ustawiając `aspNetCompatibilityEnabled` atrybutu [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) do `true`.  
  
- Komunikat tryb zabezpieczeń jest używany.  
  
 Obejście polega na wyłączeniu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] w trybie zgodności. Lub, jeśli [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności jest wymagany, wyłącz [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] personifikacji funkcji i zamiast tego należy używać personifikacji dostarczone do usług WCF. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Błąd literału adres IPv6  
 Żądania zabezpieczeń zakończyć się niepowodzeniem, klient i usługa znajdują się na tym samym komputerze, gdy literał adresy IPv6 są używane przez usługę.  
  
 Literał IPv6 adresów pracy, jeśli usługi i klienta znajdują się na różnych komputerach.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Błędy pobierania WSDL za pomocą zaufania federacyjnego  
 Usługi WCF wymaga dokładnie jednego dokumentu WSDL dla każdego węzła w łańcuchu zaufania federacyjnego. Uważaj, aby nie skonfigurować pętlę podczas określania punktów końcowych. Jednym ze sposobów, w którym mogą wystąpić pętli używa do pobrania WSDL łańcuchów zaufania federacji z co najmniej dwóch łączy w tym samym dokumencie WSDL. Typowy scenariusz, które może powodować problem jest usługi federacyjnej, gdzie serwer tokenu zabezpieczeń i usługi znajdują się wewnątrz tego samego elementu ServiceHost.  
  
 Przykładem takiej sytuacji jest usługą zawierającą następujące trzy adresy punktów końcowych:  
  
- `http://localhost/CalculatorService/service` (usługa)  
  
- `http://localhost/CalculatorService/issue_ticket` (STS)  
  
- `http://localhost/CalculatorService/mex` (punkt końcowy metadanych)  
  
 To zgłasza wyjątek.  
  
 Możesz wprowadzić w tym scenariuszu, praca, umieszczając `issue_ticket` punktu końcowego w innym miejscu.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Atrybuty importu WSDL mogą być utracone  
 WCF traci śledzenie atrybutów na `<wst:Claims>` element `RST` szablonu w trakcie importu WSDL. To będzie się działo podczas importu WSDL w przypadku określenia `<Claims>` bezpośrednio w `WSFederationHttpBinding.Security.Message.TokenRequestParameters` lub `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` zamiast bezpośrednio przy użyciu kolekcji typów oświadczeń.  Ponieważ importu utraci atrybuty, powiązanie nie obiegu poprawnie za pośrednictwem WSDL i dlatego jest niepoprawna po stronie klienta.  
  
 Obejście polega na modyfikowanie wiązanie bezpośrednio na komputerze klienckim po wykonaniu tej importu.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
