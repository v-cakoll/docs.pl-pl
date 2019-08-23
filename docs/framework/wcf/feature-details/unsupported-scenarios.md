---
title: Nieobsługiwane scenariusze
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: cc40ccbf83e92404dca07344fae0a6f56f92cefa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955321"
---
# <a name="unsupported-scenarios"></a>Nieobsługiwane scenariusze
Z różnych powodów Windows Communication Foundation (WCF) nie obsługuje niektórych określonych scenariuszy zabezpieczeń. Na przykład [!INCLUDE[wxp](../../../../includes/wxp-md.md)] wersja Home Edition nie implementuje protokołów uwierzytelniania SSPI ani protokołu Kerberos, dlatego program WCF nie obsługuje uruchamiania usługi z uwierzytelnianiem systemu Windows na tej platformie. Inne mechanizmy uwierzytelniania, takie jak nazwa użytkownika i hasło oraz zintegrowane uwierzytelnianie HTTP/HTTPS, są obsługiwane w przypadku uruchamiania programu WCF w systemie Windows XP Home Edition.  
  
## <a name="impersonation-scenarios"></a>Scenariusze personifikacji  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>Personifikowana tożsamość może nie przepływać, gdy klienci powodują wywołania asynchroniczne  
 Gdy klient WCF wykonuje wywołania asynchroniczne do usługi WCF przy użyciu uwierzytelniania systemu Windows w ramach personifikacji, uwierzytelnianie może wystąpić w przypadku tożsamości procesu klienta zamiast personifikowanej tożsamości.  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Włączono plik cookie systemu Windows XP i bezpiecznego tokenu kontekstu  
 Funkcja WCF nie obsługuje personifikacji i <xref:System.InvalidOperationException> jest zgłaszany, gdy istnieją następujące warunki:  
  
- System operacyjny to [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
- Tryb uwierzytelniania powoduje tożsamość systemu Windows.  
  
- Właściwość obiektu ma ustawioną wartość <xref:System.ServiceModel.ImpersonationOption.Required>. <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> <xref:System.ServiceModel.OperationBehaviorAttribute>  
  
- Tworzony jest token kontekstu zabezpieczeń oparty na stanie (SCT) (domyślnie tworzenie jest wyłączone).  
  
 Plik SCT oparty na stanie można utworzyć tylko przy użyciu niestandardowego powiązania. Aby uzyskać więcej informacji, zobacz [jak: Utwórz token kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md). W kodzie, token jest włączony przez utworzenie elementu powiązania <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> zabezpieczeń ( <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>albo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType> ) przy użyciu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> lub metody i ustawienie `requireCancellation` parametru na `false`. Parametr odnosi się do buforowania SCT. Ustawienie wartości `false` powoduje włączenie funkcji SCT opartej na stanie.  
  
 Alternatywnie, w konfiguracji, token jest włączony`customBinding`przez utworzenie > <, a następnie dodanie `authenticationMode` elementu <`security`> i ustawienie atrybutu na SecureConversation i `requireSecurityContextCancellation` atrybut na `true`.  
  
> [!NOTE]
> Powyższe wymagania są specyficzne. Na przykład <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> tworzy element powiązania, który powoduje tożsamość systemu Windows, ale nie ustanawia SCT. Z `Required` tego względu można użyć opcji w [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
### <a name="possible-aspnet-conflict"></a>Możliwy konflikt ASP.NET  
 Funkcje WCF i ASP.NET mogą włączać lub wyłączać personifikację. Gdy usługa ASP.NET obsługuje aplikację WCF, może istnieć konflikt między ustawieniami konfiguracji programu WCF i ASP.NET. W przypadku konfliktu ustawienie WCF ma pierwszeństwo, chyba że <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> właściwość jest ustawiona na <xref:System.ServiceModel.ImpersonationOption.NotAllowed>, w tym przypadku ustawienie personifikacji ASP.net ma pierwszeństwo.  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>Obciążenia zestawu mogą się nie powieść w ramach personifikacji  
 Jeśli personifikowany kontekst nie ma uprawnień dostępu do ładowania zestawu i jeśli jest to pierwsze środowisko uruchomieniowe języka wspólnego (CLR) próbuje załadować zestaw dla tej domeny, <xref:System.AppDomain> pamięć podręczna jest niepowodzenie. Kolejne próby załadowania zestawu (lub zestawów) kończą się niepowodzeniem nawet po powróceniu personifikacji, a nawet jeśli cofnięty kontekst ma prawa dostępu do ładowania zestawu. Dzieje się tak, ponieważ środowisko CLR nie próbuje ponownie załadować po zmianie kontekstu użytkownika. Aby odzyskać sprawność po awarii, należy ponownie uruchomić domenę aplikacji.  
  
> [!NOTE]
> Wartość <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> domyślna właściwości <xref:System.ServiceModel.Security.WindowsClientCredential> klasy to <xref:System.Security.Principal.TokenImpersonationLevel.Identification>. W większości przypadków kontekst personifikacji na poziomie tożsamości nie ma praw do ładowania żadnych dodatkowych zestawów. Jest to wartość domyślna, więc jest to bardzo typowy warunek, z którym należy się zapoznać. Personifikacja na poziomie tożsamości występuje również wtedy, gdy proces personifikacji nie ma `SeImpersonate` uprawnień. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
### <a name="delegation-requires-credential-negotiation"></a>Delegowanie wymaga negocjowania poświadczeń  
 Aby użyć protokołu uwierzytelniania Kerberos z delegowaniem, należy zaimplementować protokół Kerberos za pomocą negocjacji poświadczeń (czasami nazywany wieloetapowym lub wieloetapowym Kerberos). W przypadku zaimplementowania uwierzytelniania przy użyciu protokołu Kerberos bez negocjowania poświadczeń (nazywanego czasem pojedynczym lub jednym etapem Kerberos) występuje wyjątek. Aby uzyskać więcej informacji na temat implementowania negocjacji poświadczeń, zobacz [Debugowanie błędów uwierzytelniania systemu Windows](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md).  
  
## <a name="cryptography"></a>Cryptography  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>Algorytm SHA-256 jest obsługiwany tylko w przypadku użycia klucza symetrycznego  
 Usługa WCF obsługuje różne algorytmy szyfrowania i tworzenia podsumowania podpisów, które można określić przy użyciu pakietu algorytmów w powiązaniach dostarczonych przez system. W celu zwiększenia bezpieczeństwa Funkcja WCF obsługuje algorytmy SHA (Secure Hash Algorithm) 2, w tym SHA-256, do tworzenia skrótów skrótu sygnatur. Ta wersja obsługuje Algorytm SHA-256 tylko dla symetrycznego użycia klucza, takich jak klucze Kerberos, oraz miejsce, w którym certyfikat X. 509 nie jest używany do podpisywania wiadomości. Usługa WCF nie obsługuje podpisów RSA (używanych w certyfikatach X. 509) przy użyciu skrótu SHA-256 z powodu bieżącego braku obsługi dla algorytmu RSA-SHA256 w programie WinFX.  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>Skróty SHA-256 zgodne ze standardem FIPS nie są obsługiwane  
 Funkcja WCF nie obsługuje skrótów zgodnych ze standardem FIPS-256, więc zestawy algorytmów używające algorytmu SHA-256 nie są obsługiwane przez funkcję WCF w systemach, w których wymagane są algorytmy zgodne ze standardem FIPS.  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>Algorytmy zgodne ze standardem FIPS mogą kończyć się niepowodzeniem, jeśli rejestr jest edytowany  
 Algorytmy zgodne z ustawieniami FIPS (Federal Information Processing Standards) można włączać i wyłączać za pomocą przystawki ustawienia zabezpieczeń lokalnych programu Microsoft Management Console (MMC). Możesz również uzyskać dostęp do ustawienia w rejestrze. Należy jednak pamiętać, że usługa WCF nie obsługuje resetowania ustawienia przy użyciu rejestru. Jeśli wartość jest ustawiona na inne niż 1 lub 0, mogą wystąpić niespójne wyniki między środowiskiem CLR i systemem operacyjnym.  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>Ograniczenie szyfrowania AES zgodne ze standardem FIPS  
 Szyfrowanie AES zgodne ze standardem FIPS nie działa w bezstronnych wywołaniach zwrotnych pod personifikacją na poziomie tożsamości.  
  
### <a name="cngksp-certificates"></a>Certyfikaty CNG/dostawcy magazynu kluczy  
 *Interfejs API kryptografii: Kolejna generacja (CNG)* jest długoterminową wymianą dla interfejsu CryptoAPI. Ten interfejs API jest dostępny w kodzie niezarządzanym w systemach [!INCLUDE[wv](../../../../includes/wv-md.md)] [!INCLUDE[lserver](../../../../includes/lserver-md.md)] i nowszych wersjach systemu Windows.  
  
 .NET Framework 4.6.1 i wcześniejsze wersje nie obsługują tych certyfikatów, ponieważ używają starszego interfejsu CryptoAPI do obsługi certyfikatów CNG/dostawcy magazynu kluczy. Użycie tych certyfikatów w .NET Framework 4.6.1 i wcześniejszych wersji spowoduje wystąpienie wyjątku.  
  
 Istnieją dwa sposoby, aby stwierdzić, czy certyfikat używa dostawcy magazynu kluczy:  
  
- Wykonaj i Zbadaj`dwProvType` zwrócone .`CertGetCertificateContextProperty` `p/invoke` `CertGetCertificateContextProperty`  
  
- `certutil` Użyj polecenia z wiersza polecenia w celu wykonywania zapytań dotyczących certyfikatów. Aby uzyskać więcej informacji, zobacz [zadania narzędzia Certutil dotyczące rozwiązywania problemów z certyfikatami](https://go.microsoft.com/fwlink/?LinkId=120056).  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>Bezpieczeństwo komunikatów kończy się niepowodzeniem, jeśli jest wymagane użycie personifikacji ASP.NET i zgodność ASP.NET  
 Usługa WCF nie obsługuje następującej kombinacji ustawień, ponieważ mogą one uniemożliwiać uwierzytelnianie klienta:  
  
- ASP.NET Personifikacja jest włączona. Jest to wykonywane w pliku Web. config przez ustawienie `impersonate` atrybutu > <`identity`elementu `true`.  
  
- Tryb zgodności ASP.NET jest włączany przez ustawienie `aspNetCompatibilityEnabled` atrybutu [ \<ServiceHostingEnvironment >.](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) `true`  
  
- Używane są zabezpieczenia w trybie komunikatów.  
  
 Obejście tego problemu polega na wyłączeniu trybu zgodności ASP.NET. Jeśli jednak wymagany jest tryb zgodności ASP.NET, należy wyłączyć funkcję personifikacji ASP.NET i zamiast tego użyć personifikacji dostarczonej przez funkcję WCF. Aby uzyskać więcej informacji, zobacz [delegowanie i personifikacja](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="ipv6-literal-address-failure"></a>Niepowodzenie adresu literału IPv6  
 Żądania zabezpieczeń kończą się niepowodzeniem, gdy klient i usługa znajdują się na tym samym komputerze, a dla usługi są używane adresy literałów IPv6.  
  
 Literały adresów IPv6 działają, jeśli usługa i klient znajdują się na różnych komputerach.  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>Błędy pobierania WSDL z zaufaniem federacyjnym  
 Funkcja WCF wymaga dokładnie jednego dokumentu WSDL dla każdego węzła w federacyjnym łańcuchu zaufania. Należy zachować ostrożność, aby nie konfigurować pętli podczas określania punktów końcowych. Jednym ze sposobów, w którym mogą wystąpić pętle, jest użycie WSDL pobrania łańcuchów zaufania federacyjnego z co najmniej dwoma łączami w tym samym dokumencie WSDL. Typowym scenariuszem, który może powodować ten problem, jest usługa federacyjna, w której serwer tokenów zabezpieczających i usługa znajdują się wewnątrz tego samego elementu ServiceHost.  
  
 Przykładem takiej sytuacji jest usługa z następującymi trzema adresami punktów końcowych:  
  
- `http://localhost/CalculatorService/service`(usługa)  
  
- `http://localhost/CalculatorService/issue_ticket`(STS)  
  
- `http://localhost/CalculatorService/mex`(punkt końcowy metadanych)  
  
 Powoduje to zgłoszenie wyjątku.  
  
 Ten scenariusz można wykonać, umieszczając punkt końcowy `issue_ticket` w innym miejscu.  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>Atrybuty importu WSDL mogą zostać utracone  
 Funkcja WCF traci śledzenie atrybutów dla `<wst:Claims>` elementu `RST` w szablonie podczas importowania WSDL. Dzieje się tak podczas importowania WSDL, jeśli określono `<Claims>` bezpośrednio w `WSFederationHttpBinding.Security.Message.TokenRequestParameters` lub `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` zamiast bezpośrednio używać kolekcji typu "Claims".  Ponieważ import utraci atrybuty, powiązanie nie jest prawidłowo przeszukiwane za pomocą języka WSDL i dlatego jest niepoprawne po stronie klienta.  
  
 Poprawka polega na zmodyfikowaniu powiązania bezpośrednio na kliencie po zaimportowaniu.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Podniesienie uprawnień](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
