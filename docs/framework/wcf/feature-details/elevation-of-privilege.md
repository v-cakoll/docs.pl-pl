---
title: Podniesienie uprawnień
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: eae3c2a72e686774ee510dfc3ec9db04df7db630
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966169"
---
# <a name="elevation-of-privilege"></a>Podniesienie uprawnień
*Podniesienie* uprawnień w wyniku udzielenia uprawnień autoryzacji osoby atakującej poza wstępnie udzielonym. Na przykład osoba atakująca z zestawem uprawnień "tylko do odczytu" w dowolnej postaci podnosi poziom w taki sposób, aby obejmował "Odczyt i zapis".  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Zaufane usługi STS powinny podpisywać oświadczenia tokenów SAML  
 Token potwierdzeń zabezpieczeń (SAML) jest ogólnym tokenem XML, który jest domyślnym typem dla wystawionych tokenów. Token SAML może być skonstruowany przez usługę tokenu zabezpieczającego (STS), którą usługa sieci Web jest zaufana w typowej wymianie. Tokeny SAML zawierają oświadczenia w instrukcjach. Osoba atakująca może skopiować oświadczenia z prawidłowego tokenu, utworzyć nowy token SAML i podpisać go innym wystawcą. Celem jest określenie, czy serwer sprawdza poprawność wystawców i, jeśli nie, użyje luki w celu skonstruowania tokenów SAML, które zezwalają na uprawnienia poza tymi, które są przeznaczone dla zaufanej usługi STS.  
  
 Klasa weryfikuje podpis cyfrowy zawarty w tokenie SAML i domyślnie <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> wymaga podpisania tokenów SAML przy użyciu certyfikatu X. 509, <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> który jest <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> prawidłowy, gdy dla klasy jest ustawiona wartość <xref:System.IdentityModel.Tokens.SamlAssertion> <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust`sam tryb jest niewystarczający, aby określić, czy Wystawca tokenu SAML jest zaufany. Usługi, które wymagają bardziej szczegółowego modelu zaufania, mogą użyć zasad autoryzacji i wymuszania do sprawdzania wystawcy zestawów roszczeń utworzonych przez uwierzytelnianie wystawionego tokenu lub użyć ustawień weryfikacji X <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> . 509 w celu ograniczenia zestawu dozwolone certyfikaty podpisywania. Aby uzyskać więcej informacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) oraz [Federacji i](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)wystawionych tokenów.  
  
## <a name="switching-identity-without-a-security-context"></a>Przełączanie tożsamości bez kontekstu zabezpieczeń  
 Poniższe zasady dotyczą tylko programu WinFX.  
  
 W przypadku ustanowienia połączenia między klientem a serwerem tożsamość klienta nie zmienia się, z wyjątkiem sytuacji, gdy jest otwarty klient WCF, jeśli spełnione są wszystkie następujące warunki:  
  
- Procedury ustanawiania kontekstu zabezpieczeń (przy użyciu sesji zabezpieczeń transportu lub sesji zabezpieczeń komunikatów) są przełączane (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> właściwość jest ustawiana na `false` wypadek zabezpieczenia komunikatów lub transport nie ma możliwości ustanowienia zabezpieczeń sesje są używane w przypadku zabezpieczeń transportu. HTTPS to jeden przykład takiego transportu).  
  
- Używasz uwierzytelniania systemu Windows.  
  
- Nie ustawiasz jawnie poświadczenia.  
  
- Wywołujesz usługę w ramach personifikowanego kontekstu zabezpieczeń.  
  
 Jeśli te warunki są spełnione, tożsamość użyta do uwierzytelnienia klienta w usłudze może ulec zmianie (może nie być to personifikowana tożsamość, ale tożsamość procesu) po otwarciu klienta programu WCF. Dzieje się tak, ponieważ poświadczenia systemu Windows używane do uwierzytelniania klienta w usłudze są przesyłane wraz z każdym komunikatem, a poświadczenia używane do uwierzytelniania są uzyskiwane z tożsamości systemu Windows bieżącego wątku. Jeśli tożsamość systemu Windows bieżącego wątku ulegnie zmianie (na przykład przez personifikację innego obiektu wywołującego), poświadczenie dołączone do wiadomości i użyte do uwierzytelnienia klienta w usłudze również może ulec zmianie.  
  
 Jeśli chcesz mieć deterministyczne zachowanie podczas korzystania z uwierzytelniania systemu Windows razem z personifikacją, musisz jawnie ustawić poświadczenia systemu Windows lub ustanowić kontekst zabezpieczeń z usługą. W tym celu należy użyć sesji zabezpieczeń wiadomości lub sesji zabezpieczeń transportu. Na przykład transport net. TCP może zapewnić sesję zabezpieczeń transportu. Ponadto podczas wywoływania usługi należy używać tylko synchronicznej wersji operacji klienta. W przypadku ustanowienia kontekstu zabezpieczeń wiadomości nie powinno być konieczne pozostawienie połączenia z usługą dłużej niż skonfigurowany okres odnawiania sesji, ponieważ tożsamość może być również zmieniana podczas procesu odnawiania sesji.  
  
### <a name="credentials-capture"></a>Przechwytywanie poświadczeń  
 Poniższe wersje dotyczą [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)]programu i kolejnych wersji.  
  
 Poświadczenia używane przez klienta lub usługę są oparte na bieżącym wątku kontekstu. Poświadczenia są uzyskiwane, gdy `Open` wywoływana jest metoda `BeginOpen`(lub, dla wywołań asynchronicznych) klienta lub usługi. <xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> Dla klas <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> i, `Open` metody i`BeginOpen` dziedziczą z metod<xref:System.ServiceModel.Channels.CommunicationObject> i klasy. <xref:System.ServiceModel.ServiceHost>  
  
> [!NOTE]
> W przypadku korzystania `BeginOpen` z metody przechwycone poświadczenia nie mogą być poświadczeniami procesu wywołującego metodę.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Pamięć podręczna tokenów zezwala na powtarzanie przy użyciu przestarzałych danych  
 Usługa WCF korzysta z funkcji urzędu zabezpieczeń lokalnych ( `LogonUser` LSA) do uwierzytelniania użytkowników według nazwy użytkownika i hasła. Ponieważ funkcja logowania jest kosztowną operacją, WCF pozwala na buforowanie tokenów reprezentujących użytkowników uwierzytelnionych w celu zwiększenia wydajności. Mechanizm buforowania zapisuje wyniki `LogonUser` dla kolejnych użycia. Ten mechanizm jest domyślnie wyłączony; Aby ją włączyć, należy ustawić <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> właściwość na `true`lub `cacheLogonTokens` [ \<użyć atrybutu userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Można ustawić czas wygaśnięcia ( <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> TTL) dla buforowanych tokenów przez ustawienie właściwości <xref:System.TimeSpan>na lub `userNameAuthentication` użyć `cachedLogonTokenLifetime` atrybutu elementu; wartość domyślna to 15 minut. Należy pamiętać, że gdy token jest buforowany, każdy klient, który przedstawia taką samą nazwę użytkownika i hasło, może używać tokenu, nawet jeśli konto użytkownika zostanie usunięte z systemu Windows lub zmieniono jego hasło. Do momentu wygaśnięcia czasu wygaśnięcia i usunięcia tokenu z pamięci podręcznej program WCF zezwoli użytkownikowi (prawdopodobnie złośliwemu) na uwierzytelnienie.  
  
 Aby wyeliminować ten problem: Zmniejszenie okna ataków przez ustawienie `cachedLogonTokenLifetime` wartości na najkrótszy czas na potrzeby użytkowników.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Autoryzacja wystawionego tokenu: Resetowanie wygaśnięcia do dużej wartości  
 W pewnych warunkach <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> Właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> może być ustawiona na <xref:System.DateTime.MaxValue> nieoczekiwaną większą wartość (wartość pola minus jeden dzień lub 20 grudnia 9999).  
  
 Dzieje się tak w przypadku <xref:System.ServiceModel.WSFederationHttpBinding> użycia i dowolnego powiązania dostarczonego przez system, które ma wystawiony token jako typ poświadczeń klienta.  
  
 Występuje to również podczas tworzenia powiązań niestandardowych przy użyciu jednej z następujących metod:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Aby temu zapobiec, zasady autoryzacji muszą sprawdzać akcję i czas wygaśnięcia poszczególnych zasad autoryzacji.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Usługa używa innego certyfikatu niż zamierzony klient  
 W pewnych warunkach klient może cyfrowo podpisać komunikat przy użyciu certyfikatu X. 509, a usługa pobiera inny certyfikat niż przewidziany.  
  
 Może się to zdarzyć w następujących okolicznościach:  
  
- Klient cyfrowo podpisuje komunikat przy użyciu certyfikatu X. 509 i nie dołącza certyfikatu X. 509 do wiadomości, ale nie tylko odwołuje się do certyfikatu przy użyciu identyfikatora klucza podmiotu.  
  
- Komputer usługi zawiera dwa lub więcej certyfikatów z tym samym kluczem publicznym, ale zawierają różne informacje.  
  
- Usługa pobiera certyfikat odpowiadający identyfikatorowi klucza podmiotu, ale nie jest to klient, którego zamierza użyć. Gdy usługa WCF odbiera komunikat i weryfikuje podpis, usługa WCF mapuje informacje w niezamierzonym certyfikacie X. 509 do zestawu oświadczeń, które są różne i mogą być podniesione z poziomu klienta.  
  
 Aby rozwiązać ten problem, należy odwołać się do certyfikatu X. 509 w inny sposób <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>, na przykład przy użyciu.  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
- [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
