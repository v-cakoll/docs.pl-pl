---
title: Podniesienie uprawnień
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: fd5829d2dbb1853bf65f1f6e402b918137bd59e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856411"
---
# <a name="elevation-of-privilege"></a>Podniesienie uprawnień
*Podniesienie uprawnień* powstały na skutek zapewniając autoryzacji osoba atakująca uprawnień poza tymi początkowo udzielone. Na przykład osoba atakująca z zestawem uprawnień uprawnienia "tylko do odczytu" jakiś sposób podnosi poziom uprawnień zestawu do uwzględnienia "odczytu i zapisu."  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Zaufana Usługa STS Utwórz oświadczeń tokenu SAML  
 Token potwierdzenia języka SAML (Security Markup) jest ogólny token XML, który jest domyślnym typem wystawianych tokenów. SAML token można konstruować przez Usługa tokenu zabezpieczającego (STS) uznającego końcowych usługi sieci Web w typowej programu exchange. Tokeny SAML zawierają oświadczenia w instrukcjach. Osoba atakująca może skopiować oświadczenia z prawidłowym tokenem, Utwórz nowy token SAML i podpisać ją przy użyciu różnych wystawcy. Celem jest określić, czy serwer jest sprawdzania poprawności wystawcy, a jeśli nie, korzystanie z słabość do konstruowania tokeny SAML, zezwalających na uprawnienia poza te zamierzony przez usługę STS zaufanych.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> Klasy weryfikuje podpis cyfrowy zawartych w tokenie języka SAML i domyślnego <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wymaga podpisania tokeny SAML, certyfikat X.509, który jest nieprawidłowy, gdy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasy jest ustawiona na <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust` Tryb samego jest za mała, aby ustalić, czy wystawca SAML token jest zaufany. Usługi, które wymagają bardziej szczegółowy model zaufania można albo użyć autoryzacji i wymuszanie zasad do sprawdzanych wystawcy zestawów oświadczeń produkowane przez uwierzytelnianie przy użyciu tokenów wystawionych lub ustawienia weryfikacji X.509 na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> ograniczyć zestaw dozwolone certyfikaty podpisywania. Aby uzyskać więcej informacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) i [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Przełączanie tożsamości bez kontekstu zabezpieczeń  
 Następujące ma zastosowanie tylko do [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Po nawiązaniu połączenia między klientem i serwerem oraz tożsamości klienta nie zmienia się, z wyjątkiem sytuacji: po otwarciu klienta WCF, jeśli spełnione są wszystkie następujące warunki:  
  
- Procedury ustanawiania kontekstu zabezpieczeń (przy użyciu zabezpieczeń transport, sesji lub sesji zabezpieczeń wiadomości) jest wyłączany (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość jest ustawiona na `false` przypadku zabezpieczenia wiadomości lub niezdolnych do ustanawiania zabezpieczeń transportu sesje są używane w przypadku zabezpieczeń transportu. Protokół HTTPS jest przykładem takiego transportu).  
  
- Korzystasz z uwierzytelniania Windows.  
  
- Nie używaj jawne poświadczenia.  
  
- Wywołujesz usługi w obszarze spersonifikowanym kontekście zabezpieczeń.  
  
 Jeśli te warunki są spełnione, to tożsamość używana do uwierzytelniania klienta do usługi mogą ulec zmianie (może nie być personifikowanej tożsamości, ale tożsamość procesu zamiast) po otwarciu klienta platformy WCF. Dzieje się tak, ponieważ poświadczenia Windows używane do uwierzytelniania klienta do usługi są przesyłane za pomocą każdej wiadomości i poświadczeń używanych do uwierzytelniania są uzyskiwane z bieżącego wątku Windows tożsamości. Jeśli zmieni tożsamość Windows bieżącego wątku (na przykład, Personifikując inny obiekt wywołujący), poświadczeń, który jest dołączony do wiadomości i używany do uwierzytelniania klienta do usługi także mogą ulec zmianie.  
  
 Jeśli chcesz mieć deterministyczne zachowanie podczas korzystania z uwierzytelniania Windows wraz z personifikacji należy jawnie ustawić poświadczenia Windows, lub należy ustanowić kontekstu zabezpieczeń w usłudze. Aby to zrobić, należy użyć sesji zabezpieczeń wiadomości lub sesja zabezpieczeń transportu. Na przykład transportu net.tcp, może zapewnić sesji zabezpieczeń transportu. Ponadto podczas wywoływania usługi należy użyć synchroniczna wersja operacji klienta. Jeśli ustanowisz kontekstu zabezpieczeń wiadomości, nie Zachowaj połączenie z usługą Otwórz dłuższy niż okres odnawiania skonfigurowanych sesji, ponieważ tożsamość można również zmienić w procesie odnawiania sesji.  
  
### <a name="credentials-capture"></a>Przechwycenie poświadczeń  
 Poniższe uwagi dotyczą [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]i późniejszych wersjach.  
  
 Poświadczenia używane przez klienta lub usługi zależą od bieżącego wątku kontekstu. Poświadczenia są uzyskiwane podczas `Open` — metoda (lub `BeginOpen`, na wywołania asynchroniczne) klienta lub usługi jest wywoływana. Dla obu <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ClientBase%601> klas, `Open` i `BeginOpen` metody dziedziczyć <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> i <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> metody <xref:System.ServiceModel.Channels.CommunicationObject> klasy.  
  
> [!NOTE]
>  Korzystając z `BeginOpen` metody, nie można zagwarantować poświadczenia przechwytywane do poświadczenia procesu, który wywołuje metodę.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Pamięci podręczne tokenu umożliwia powtarzanie przy użyciu przestarzałe dane  
 Urząd zabezpieczeń lokalnych (LSA) korzysta z usługi WCF `LogonUser` funkcję, aby uwierzytelniać użytkowników według nazwy użytkownika i hasło. Ponieważ funkcja logowania jest kosztowna operacja, WCF umożliwia do pamięci podręcznej tokenów, które reprezentują uwierzytelnionych użytkowników, co pozwoli zwiększyć wydajność. Mechanizm buforowania zapisuje wyniki z `LogonUser` do późniejszego wykorzystania. Ten mechanizm jest domyślnie wyłączona; Aby ją włączyć, ustaw <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> właściwości `true`, lub użyj `cacheLogonTokens` atrybutu [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Można ustawić czas wygaśnięcia (TTL) dla pamięci podręcznej tokeny, ustawiając <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> właściwości <xref:System.TimeSpan>, lub użyj `cachedLogonTokenLifetime` atrybutu `userNameAuthentication` element; wartość domyślna to 15 minut. Pamiętaj, że gdy token są buforowane, każdy klient, który przedstawia informacje o tej samej nazwy użytkownika i hasła można używać tokenu, nawet, jeśli konto użytkownika zostanie usunięte z Windows lub zmieniono jego hasło. Do momentu wygaśnięcia i token zostanie usunięty z pamięci podręcznej, WCF umożliwia uwierzytelnienia użytkownika (potencjalnie złośliwego).  
  
 Aby rozwiązać ten problem: Zmniejsz okna ataku, ustawiając `cachedLogonTokenLifetime` wartość przez jak najkrótszy czas span Twoich potrzeb użytkowników.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Wystawiony Token autoryzacji: Resetowanie wygaśnięcia duża wartość  
 Pod pewnymi warunkami <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> może być ustawiona na wartość nieoczekiwanie większe ( <xref:System.DateTime.MaxValue> pola wartości, minus jeden dzień lub 20 grudnia 9999).  
  
 Ten problem wystąpi w przypadku korzystania z <xref:System.ServiceModel.WSFederationHttpBinding> i żadnego powiązania dostarczane przez system, które mają wystawiony token, którego typ poświadczeń.  
  
 Dzieje się tak również podczas tworzenia powiązań niestandardowych przy użyciu jednej z następujących metod:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Aby rozwiązać ten problem, zasady autoryzacji sprawdzić akcji i czas wygaśnięcia poszczególnych zasad autoryzacji.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Usługa używa innego certyfikatu niż zamierzano klienta  
 Pod pewnymi warunkami klienta można cyfrowego podpisywania wiadomości za pomocą certyfikatu X.509 i usługa pobieranie certyfikatu innego niż zamierzony.  
  
 Taka sytuacja może wystąpić w następujących okolicznościach:  
  
- Klient podpisuje cyfrowo komunikat przy użyciu certyfikatu X.509 nie dołączy certyfikatu X.509 do wiadomości, a zamiast po prostu odwołuje się do certyfikatu, używając swojego identyfikatora klucza podmiotu.  
  
- Komputer z usługą zawiera co najmniej dwóch certyfikatów przy użyciu tego samego klucza publicznego, ale mogą zawierać różne informacje.  
  
- Usługa pobiera certyfikat, który pasuje do identyfikatora klucza podmiotu, ale nie jest ten, który klient jest przeznaczony do użycia. Gdy WCF odbiera komunikat i weryfikuje podpis, WCF mapuje informacje zawarte w niezamierzony certyfikatu X.509 do zestawu oświadczeń, które są różne i potencjalnie z podwyższonym poziomem uprawnień z oczekiwaniami klienta.  
  
 Aby temu zaradzić, odwołanie X.509 certyfikatu inny sposób, na przykład za pomocą <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
