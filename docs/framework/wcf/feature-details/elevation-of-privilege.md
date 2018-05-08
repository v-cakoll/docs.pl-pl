---
title: Podniesienie uprawnień
ms.date: 03/30/2017
helpviewer_keywords:
- elevation of privilege [WCF]
- security [WCF], elevation of privilege
ms.assetid: 146e1c66-2a76-4ed3-98a5-fd77851a06d9
ms.openlocfilehash: c71936d087ef046848c75d1fa0638aaafbe43c9a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="elevation-of-privilege"></a>Podniesienie uprawnień
*Podniesienie uprawnień* wynikiem nadanie uprawnień poza tymi początkowo nadanego pozwolenia osoby atakującej. Na przykład osoba atakująca z zestawem uprawnień uprawnienia "tylko do odczytu" jakiś sposób eksponuje zestaw "odczytu i zapisu."  
  
## <a name="trusted-sts-should-sign-saml-token-claims"></a>Zaufane STS Utwórz oświadczeń tokenu SAML  
 Token zabezpieczeń potwierdzenia Markup Language (SAML) jest ogólny tokenu XML, który jest domyślnym typem dla wystawionych tokenów. Można utworzyć tokenu SAML przez zabezpieczeń tokenu usługi (STS), która końcowy usługi sieci Web zaufania w typowych programu exchange. Tokeny SAML zawierają oświadczeń w instrukcjach. Osoba atakująca może skopiować oświadczenia z prawidłowym tokenem, Utwórz nowy token SAML i podpisz go za pomocą różnych wystawcy. Celem jest określić, czy serwer jest sprawdzania poprawności wystawcy i, jeśli nie, wykorzystania słabe do utworzenia tokenów SAML, zezwalających na uprawnienia poza tych przeznaczonych przez zaufany STS.  
  
 <xref:System.IdentityModel.Tokens.SamlAssertion> Klasy weryfikuje podpis cyfrowy zawartych w tokenie SAML i domyślnie <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> tokeny SAML musi być zarejestrowany przez certyfikatu X.509, który jest prawidłowa, gdy <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> z <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> klasa ma ustawioną wartość <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust>. `ChainTrust` Tryb samego jest za mało, aby ustalić, czy Wystawca tokenu SAML jest zaufany. Usługi, które wymagają bardziej szczegółowego model zaufania można albo użyć zasad autoryzacji i wymuszania aby wystawcę zestawów oświadczeń, utworzonego przez wystawionego tokenu uwierzytelniania lub ustawienia weryfikacji X.509 na <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> ograniczyć zestaw dozwolone certyfikaty podpisywania. Aby uzyskać więcej informacji, zobacz [Zarządzanie oświadczeniami i autoryzacją za pomocą modelu tożsamości](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md) i [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="switching-identity-without-a-security-context"></a>Przełączanie tożsamości bez kontekstu zabezpieczeń  
 Następujące dotyczą tylko [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Po nawiązaniu połączenia między klientem a serwerem, tożsamość klienta nie ulega zmianie, z wyjątkiem sytuacji jeden: po otwarciu klienta platformy WCF, jeśli spełnione są wszystkie poniższe warunki:  
  
-   Procedury, aby ustanowić kontekst zabezpieczeń (za pomocą zabezpieczeń transportu, sesji lub sesji zabezpieczeń wiadomości) jest wyłączany (<xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> ma ustawioną wartość właściwości `false` w przypadku zabezpieczenia komunikatów lub nie mogą ustanawianie zabezpieczeń transportu sesje są używane w przypadku zabezpieczeń transportu. Przykładem takiego transportu jest HTTPS).  
  
-   Korzystasz z uwierzytelniania systemu Windows.  
  
-   Nie ustawiaj jawnie poświadczenie.  
  
-   Usługi w kontekście zabezpieczeń personifikowanej są wywoływania.  
  
 Jeśli te warunki są spełnione, mogą ulec zmianie tożsamości używanej do uwierzytelniania klienta do usługi (może nie być personifikowanej tożsamości, ale tożsamość procesu zamiast) po otwarciu klienta platformy WCF. Dzieje się tak, ponieważ poświadczenia systemu Windows używane do uwierzytelniania klienta do usługi jest przekazywany z każdej wiadomości i poświadczeń używanych do uwierzytelniania są uzyskiwane z bieżącego wątku tożsamości systemu Windows. Zmiana tożsamości systemu Windows w bieżącym wątku (na przykład przez personifikacji wywołującego różnych) również może zmienić poświadczeń, który jest dołączony do wiadomości i używany do uwierzytelniania klienta do usługi.  
  
 Jeśli mają deterministyczne zachowanie, gdy jest używane uwierzytelnianie systemu Windows wraz z personifikacji należy jawnie ustawić poświadczenia systemu Windows lub należy ustanowić kontekst zabezpieczeń w usłudze. Aby to zrobić, użyj sesji zabezpieczeń wiadomości lub sesji zabezpieczeń transportu. Na przykład transportu net.tcp zapewniają sesji zabezpieczeń transportu. Ponadto należy używać synchroniczną wersję operacje klienta podczas wywoływania usługi. Po nawiązaniu kontekstu zabezpieczeń wiadomości nie Zachowaj połączenie z usługą Otwórz dłuższy niż okres odnawiania skonfigurowanych sesji, ponieważ tożsamość można również zmienić podczas procesu odnowienia sesji.  
  
### <a name="credentials-capture"></a>Poświadczenia przechwytywania  
 Poniższe uwagi dotyczą [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)], a w kolejnych wersjach.  
  
 Poświadczenia używane przez klienta lub usługi są oparte na bieżący wątek kontekstu. Poświadczenia są uzyskiwane podczas `Open` — metoda (lub `BeginOpen`, na wywołania asynchroniczne) klienta lub usługi jest wywoływana. Dla obu <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.ClientBase%601> klas, `Open` i `BeginOpen` metody dziedziczyć <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> i <xref:System.ServiceModel.Channels.CommunicationObject.BeginOpen%2A> metody <xref:System.ServiceModel.Channels.CommunicationObject> klasy.  
  
> [!NOTE]
>  Korzystając z `BeginOpen` metody, nie można zagwarantować poświadczenia przechwycone się poświadczenia proces, który wywołuje metodę.  
  
## <a name="token-caches-allow-replay-using-obsolete-data"></a>Zezwalaj na tokenu pamięć podręczną powtarzania przy użyciu danych przestarzałe  
 Urząd zabezpieczeń lokalnych (LSA) używa WCF `LogonUser` funkcji do uwierzytelniania użytkowników według nazwy użytkownika i hasła. Ponieważ funkcja logowania jest kosztowna operacja, WCF pozwala na tokeny pamięci podręcznej, które reprezentują uwierzytelnionych użytkowników w celu zwiększenia wydajności. Mechanizm buforowania zapisuje wyniki z `LogonUser` dla kolejnych zastosowań. Ten mechanizm jest domyślnie wyłączona; Aby go włączyć, ustaw <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CacheLogonTokens%2A> właściwości `true`, lub użyj `cacheLogonTokens` atrybutu [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md).  
  
 Można ustawić czas wygaśnięcia (TTL) dla pamięci podręcznej tokenów przez ustawienie <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.CachedLogonTokenLifetime%2A> właściwości <xref:System.TimeSpan>, lub użyj `cachedLogonTokenLifetime` atrybutu `userNameAuthentication` element; wartość domyślna to 15 minut. Należy pamiętać, że podczas tokenu są buforowane, każdy klient, który przedstawia informacje o tej samej nazwy użytkownika i hasła można użyć tokenu, nawet jeśli konto użytkownika zostanie usunięte z systemu Windows lub jego hasło zostało zmienione. Dopiero po wygaśnięciu czas wygaśnięcia i token zostanie usunięty z pamięci podręcznej, WCF umożliwia uwierzytelnienia użytkownika (potencjalnie szkodliwymi).  
  
 Aby temu zaradzić: zmniejszyć okno ataku przez ustawienie `cachedLogonTokenLifetime` wartość najkrótszym czasie span potrzeb użytkowników.  
  
## <a name="issued-token-authorization-expiration-reset-to-large-value"></a>Wystawiony Token autoryzacji: Resetowanie wygaśnięcia duża wartość  
 W niektórych warunkach <xref:System.IdentityModel.Policy.AuthorizationContext.ExpirationTime%2A> właściwość <xref:System.IdentityModel.Policy.AuthorizationContext> może być ustawiony na wartość nieoczekiwanie większych ( <xref:System.DateTime.MaxValue> pola wartość minus jeden dzień lub 20 grudnia 9999).  
  
 Dzieje się tak, korzystając z <xref:System.ServiceModel.WSFederationHttpBinding> i wszelkie powiązań dostarczane przez system, które mają wystawionego tokenu, co klient typ poświadczeń.  
  
 Występuje także podczas tworzenia niestandardowego powiązania za pomocą jednej z następujących metod:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>  
  
 Aby temu zaradzić, zasady autoryzacji musi sprawdzić akcji i czas wygaśnięcia każdej zasady autoryzacji.  
  
## <a name="the-service-uses-a-different-certificate-than-the-client-intended"></a>Usługa używa inny certyfikat niż przeznaczone klienckich  
 W niektórych warunkach klient może cyfrowe podpisywanie wiadomości za pomocą certyfikatu X.509 i pobrać inny certyfikat niż przeznaczone do usługi.  
  
 Taka sytuacja może wystąpić w następujących okolicznościach:  
  
-   Klient podpisaniu wiadomości przy użyciu certyfikatu X.509 nie dołączenia certyfikatu X.509 do wiadomości, a raczej właśnie odwołuje się przy użyciu swojego identyfikatora klucza podmiotu certyfikatu.  
  
-   Komputer z usługą zawiera co najmniej dwa certyfikaty z tym samym kluczem publicznym, ale mogą zawierać różne informacje.  
  
-   Usługa pobiera certyfikat, który jest zgodny z identyfikatorem klucza podmiotu, ale nie jest ten, który klient przeznaczonych do użycia. Gdy WCF odbiera wiadomości i weryfikuje podpis, WCF mapuje informacje w niezamierzone certyfikatu X.509 do zestawu oświadczeń, które są różne i potencjalnie z podwyższonym poziomem uprawnień z klienta oczekuje.  
  
 Aby temu zaradzić, X.509 odwołania certyfikatów w inny sposób, na przykład za pomocą <xref:System.ServiceModel.Security.Tokens.X509KeyIdentifierClauseType.IssuerSerial>.  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Ujawnianie informacji](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Odmowa usługi](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Ataki oparte na metodzie powtórzeń](../../../../docs/framework/wcf/feature-details/replay-attacks.md)  
 [Manipulowanie](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nieobsługiwane scenariusze](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
