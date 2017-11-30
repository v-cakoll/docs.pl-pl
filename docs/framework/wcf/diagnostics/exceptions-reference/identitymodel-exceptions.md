---
title: "Wyjątki modelu IdentityModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1f7e42d0da5a0265ef4fb63dfe59e050784e959
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="identitymodel-exceptions"></a>Wyjątki modelu IdentityModel
W tym temacie wymieniono wszystkie wyjątki generowane przez modelu IdentityModel.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Bieżący ciąg|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Wartość tego argumentu musi być jedną z tych dwóch typów.|  
|SAMLSubjectNameIdentifierRequiresNameValue|Atrybut "Name" określona dla elementu SamlNameIdentifier nie może być zerowy lub jego długość wynosi 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|Metoda IssuanceTokenProvider zakończyła negocjację zabezpieczeń.|  
|TraceCodeSecurityNewServerSessionKeyIssued|Sesję zabezpieczeń nowy klucz został wystawiony przez serwer.|  
|SAMLAttributeMissingNameAttributeOnRead|Brak "Name" dla elementu SamlAttribute lub jego długość wynosi 0.|  
|UnknownICryptoType|Implementacja interfejsu ICrypto nie jest obsługiwane.|  
|TraceCodeSecurityTokenProviderClosed|Zamknięto dostawcę tokenów zabezpieczających.|  
|SAMLUnableToLoadAdvice|Nie można załadować \<saml:advice > elementu.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Atrybut "AuthenticationMethod" odczytu elementu SamlAuthenticationStatement lub jego długość wynosi 0.|  
|UnsupportedTransformAlgorithm|Nieobsługiwany algorytm przekształcenia lub zapewniania kanoniczności.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Obiekt SamlAudienceRestrictionCondition musi zawierać co najmniej jednego odbiorcy (URI).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence musi odwoływać się do co najmniej jednego elementu SamlAssertion za pomocą identyfikatora lub odwołania.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Obiekt SamlAudienceRestrictionCondition brakuje wartości w elemencie "Audience".|  
|X509ChainBuildFail|Określone tworzenia łańcucha certyfikatu X.509 nie powiodło się. Certyfikat, który został użyty ma łańcuch zaufania, którego nie można zweryfikować. Zastąp certyfikat, lub zmień tryb certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|Nie można odnaleźć w ciągu słownikowym identyfikator określonej wartości.|  
|TraceCodeImportSecurityChannelBindingEntry|Uruchamianie metody zabezpieczeń ImportChannelBinding.|  
|PrivateKeyExchangeNotSupported|Klucz prywatny nie obsługuje wymiany KeySpec.|  
|TokenProviderUnableToGetToken|Określonego dostawcy tokenu nie była w stanie tokenu zabezpieczającego.|  
|SAMLEntityCannotBeNullOrEmpty|Określonej jednostki SamlAssertion nie może być zerowa lub pusta.|  
|SAMLAssertionRequireOneStatement|Element SamlAssertion wymaga co najmniej jedną instrukcję. Upewnij się, że dodano co najmniej jedną instrukcję SamlStatement SamlAssertion tworzenia.|  
|AESInvalidInputBlockSize|Rozmiar wejściowy musi być wielokrotnością liczby określonych bajtów.|  
|AESCryptAcquireContextFailed|Nie można pobrać kontekstu CSP.|  
|SAMLAssertionRequireOneStatementOnRead|Odczytywanego nie zawiera żadnej instrukcji SamlStatement. Element SamlAssertion musi zawierać co najmniej jedną instrukcję SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|Sesja zabezpieczeń klienta otrzymała błąd zamkniętej sesji z serwera.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|Metoda IssuanceTokenProvider zastosowała nagłówek przekierowania.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Wystąpił błąd podczas wysyłania sesji zabezpieczeń zamknięte błędów do klienta.|  
|ValueMustBeZero|Wartość tego argumentu musi wynosić 0.|  
|SAMLUnableToResolveSignatureKey|Nie można rozpoznać identyfikatora SecurityKeyIdentifier znalezionego w podpisie elementu SamlAssertion. Nie można zweryfikować podpisu SamlAssertion określonych wystawcy.|  
|X509IsNotInTrustedStore|Określonego certyfikatu X.509 nie jest w magazynie zaufanych osób.|  
|SAMLElementNotRecognized|Konkretny element nie jest obsługiwane.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|Atrybutu "Resource" brakuje elementu SamlAuthorizationDecisionStatement lub jego długość wynosi 0.|  
|SamlTokenMissingSignature|Element SamlAssertion nie jest podpisany. Element SamlAssertions może być podpisany przez ustawienie elementu SigningCredentials.|  
|ExpectedElementMissing|Brak oczekiwanego elementu z określonego obszaru nazw.|  
|NoKeyIdentifierClauseFound|Nie klauzuli określonego typu został znaleziony w identyfikatorze SecurityKeyIdentifier.|  
|MissingPrivateKey|Nie ma klucza prywatnego certyfikatu X.509.|  
|UnexpectedEOFFromReader|Nieoczekiwany koniec pliku z modułu odczytującego XML.|  
|UnsupportedKeyDerivationAlgorithm|Algorytm wyprowadzania klucza określonego nie jest obsługiwany.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Określony token nie obsługuje tworzenia klauzuli identyfikatora określonego klucza.|  
|LastMessageNumberExceeded|Wykryto naruszenie protokołu liczby sekwencji.|  
|SymmetricKeyLengthTooShort|Długość klucza symetrycznego jest za krótki.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|Odczytywany element SamlAuthorityBinding zawiera atrybut "AuthorityKind", którego brakowało lub jego długość wynosi 0.  Jest to niedozwolone.|  
|XmlTokenBufferIsEmpty|Element XmlTokenBuffer jest pusty.|  
|InvalidXmlQualifiedName|Oczekiwano nazwy kwalifikowanej Xml, ale znaleziono nieprawidłową nazwę.|  
|SAMLAuthorityKindMissingName|Element XmlQualifiedName reprezentujący "AuthorityKind" w SamlAuthorityBinding nie może być zerowy lub jego długość wynosi 0.|  
|AESCryptEncryptFailed|Nie można zaszyfrować określonych danych.|  
|AuthorizationContextCreated|Utworzono kontekst autoryzacji o określonym identyfikatorze.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|Element SamlSerializer nie zawiera elementu SecurityTokenSerializer zdolnego do odczytywania identyfikatora SecurityKeyIdentifier. Jeśli używasz niestandardowego identyfikatora SecurityKeyIdentifier należy podać niestandardowy element SecurityTokenSerializer.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|Metoda IssuanceTokenProvider zmniejszona pamięć podręczną tokenów usług.|  
|TraceCodeSecurityTokenProviderOpened|Otwarto dostawcę tokenów zabezpieczających.|  
|PublicKeyNotRSA|Klucz publiczny nie jest kluczem RSA.|  
|InvalidReaderState|Określony stan jest nieprawidłowy dla dostarczonego czytnika danych wejściowych.|  
|UnableToResolveReferenceUriForSignature|Nie można rozpoznać określonego identyfikatora URI w podpisie Aby obliczyć wartość skrótu.|  
|EmptyBase64Attribute|Znaleziono pustą wartość base64 wymaganego atrybutu nazwy i przestrzeni nazw.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SAML SubjectConfirmation wymaga stosowania metody potwierdzenia, gdy dane potwierdzenia lub KeyInfo jest określona.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|Obiekt SamlAudienceRestrictionCondition musi zawierać wartość co najmniej jednego odbiorcy. Nie znaleziono żadnych.|  
|TokenProviderUnableToRenewToken|Określonego dostawcy tokenu nie może odnowić tokenu zabezpieczającego.|  
|AESIVLengthNotSupported|IV określonej usługi bits nie jest obsługiwane. Obsługiwane jest tylko IV 128 bitów.|  
|SAMLAuthorityBindingMissingAuthorityKind|Element SamlAuthorityBinding musi zawierać atrybut "AuthorityKind" nie jest to wartość null.|  
|TraceCodeSecuritySessionDemuxFailure|Komunikat przychodzący nie jest częścią istniejącej sesji zabezpieczeń.|  
|TokenRenewalNotSupported|Określonego dostawcy tokenu nie obsługuje odnawiania tokenów.|  
|AtLeastOneReferenceRequired|Co najmniej jedno odwołanie jest wymagane w podpisie.|  
|SAMLSignatureAlreadyRead|Podpis jest już do odczytu w potwierdzenia języka SAML.|  
|AlgorithmAndPrivateKeyMisMatch|Określony algorytm i klucz prywatny są niezgodne.|  
|EmptyTransformChainNotSupported|Pusty łańcuch przekształcenia nie jest obsługiwane.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper &#124; " Przesunięcie "jest poza zakresem.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper &#124; " rozmiar "jest poza zakresem. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = zabezpieczeń Menedżer tokenów nie może utworzyć wystawcy uwierzytelnienia tokenu dla wymagania określone.|  
|UnableToCreateKeyedHashAlgorithm|Nie można utworzyć elementu KeyedHashAlgorithm z określonej wartości dla określonej sygnatury algorytmu.|  
|SAMLUnableToLoadAssertion|\<Saml:assertion > nie można załadować elementu.|  
|X509FindValueMismatchMulti|Określone X509FindType wymaga, aby typ findValue argument jedną z wartości 2. Argument findValue jest innego typu.|  
|TraceCodeSecurityIdentityDeterminationSuccess|EndpointAddress został określić tożsamości.|  
|UndefinedUseOfPrefixAtElement|Określone prefiks, który jest używany w elemencie nie ma zdefiniowanych obszaru nazw.|  
|TraceCodeSecuritySessionResponderOperationFailure|Operacja sesji zabezpieczeń nie powiodła się na serwerze.|  
|CannotFindCert|Nie można odnaleźć certyfikatu X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|Określony czas użycia certyfikatu X.509 jest nieprawidłowy. Czas użytkowania nie znajduje się między wymagany nie wcześniej niż czas i nie później niż czas.|  
|TraceCodeSecurityIdentityDeterminationFailure|Nie można określić tożsamości EndpointAddress.|  
|AsyncObjectAlreadyEnded|Metoda End została już wywołana dla tego obiektu wynik asynchroniczny.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Zewnętrzny słownik nie zawiera definicji dla wszystkich wymaganych ciągów. Określony ciąg nie jest dostępna w słowniku zdalnego.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|Sesja zabezpieczeń klienta otrzymała błąd odnowienia klucza z serwera.|  
|SAMLActionNameRequired|Ciąg, który reprezentuje SamlAction nie może być zerowy lub jego długość wynosi 0.|  
|SignatureVerificationFailed|Nie można zweryfikować podpisu.|  
|TraceCodeSecurityContextTokenCacheFull|Pamięć podręczna elementu SecurityContextSecurityToken jest pełna.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|Brak atrybutu MajorVersion odczytywanego brakuje lub jego długość wynosi 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Ten konstruktor SamlAttribute musi mieć prawo żądania wartość system.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|Oceny zasad o określonym identyfikatorze.|  
|SAMLUnableToLoadCondtions|\<Saml:conditions > nie można załadować elementu.|  
|AESKeyLengthNotSupported|Klucz określonego usługi bits nie jest obsługiwany. Tylko 128, 192 i 256 bitów klucza jest obsługiwana.|  
|UserNameCannotBeEmpty|Nazwa użytkownika nie może być pusta.|  
|AlgorithmAndPublicKeyMisMatch|Określony algorytm i klucz publiczny nie są zgodne.|  
|SAMLUnableToLoadCondtion|\<Saml:conditions > nie można załadować elementu.|  
|SamlAssertionMissingSigningCredentials|Nie ustawiono atrybutu SigningCredentials dla elementu SamlAssertion. Element SamlAssertions musi być podpisana, Ustaw prawidłową elementu SigningCredentials SamlAssertion, aby kontynuować.|  
|SspiPayloadNotEncrypted|Dane binarne nie została zaszyfrowana przy kontekstu zabezpieczeń SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|Odczytywany element SamlAuthorizationDecisionStatement nie zawiera żadnego elementu SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Protokół zabezpieczeń nie może zabezpieczyć komunikatu wychodzącego.|  
|UndefinedUseOfPrefixAtAttribute|Prefiks określonych na określony atrybut nie ma zdefiniowanych obszaru nazw.|  
|NoInputIsSetForCanonicalization|Nie ustawiono wejścia do zapisywania danych wyjściowych w postaci kanonicznej.|  
|TraceCodeSecurityPendingServerSessionAdded|Oczekująca sesja zabezpieczeń dodaje się do serwera.|  
|AsyncCallbackException|Element AsyncCallback spowodował wyjątek.|  
|PrivateKeyNotRSA|Klucz prywatny nie jest kluczem RSA.|  
|Zawierająca instrukcję TraceCodeSecurityClientSessionKeyRenewed|Sesja zabezpieczeń klienta odnowiła klucz sesji.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|"Decyzja" brakuje elementu SamlAuthorizationDecisionStatement lub jego długość wynosi 0.|  
|SAMLAttributeNameAttributeRequired|Atrybut "Name" określony dla elementu SamlAttribute nie może być zerowy lub jego długość wynosi 0.|  
|SamlSerializerRequiresExternalSerializers|Element SamlSerializer wymaga elementu SecurityTokenSerializer, aby szeregować identyfikator SecurityKeyIdentifier obecny w tokenie.|  
|UnableToResolveKeyReference|Program rozpoznawania nazw tokenów nie może rozpoznać odwołania do klucza zabezpieczeń.|  
|UnsupportedKeyWrapAlgorithm|Algorytm zawijania określonego klucza nie jest obsługiwany.|  
|SAMLAssertionMissingIssuerAttributeOnRead|Brak "Wystawca" odczytywanego lub jego długość wynosi 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|Metoda IssuanceTokenProvider użyła tokenu usługi z pamięci podręcznej.|  
|AESCryptGetKeyParamFailed|Nie można pobrać określonego parametru klucza.|  
|InvalidNamespaceForEmptyPrefix|Przestrzeń nazw jest nieprawidłowy dla pustego prefiksu.|  
|AESCipherModeNotSupported|Tryb określonych szyfrowania nie jest obsługiwany. Obsługiwane jest tylko CBC.|  
|ArgumentCannotBeEmptyString|Argument musi być niepustym ciągiem.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|Brak MinorVersion dla odczytywanego lub jego długość wynosi 0.|  
|SpecifiedStringNotAvailableInDictionary|Określony ciąg nie jest w słowniku bieżącego wpisu.|  
|KerberosApReqInvalidOrOutOfMemory|Kerberos jest nieprawidłowy lub system nie ma wystarczającej ilości pamięci.|  
|FailLogonUser|Funkcji LogonUser nie powiodło się dla określonego użytkownika. Upewnij się, że użytkownik ma prawidłowe konto systemu Windows.|  
|ValueMustBeNonNegative|Wartość tego argumentu musi być nieujemna.|  
|X509ValidationFail|Sprawdzanie poprawności określonego certyfikatu X.509 nie powiodło się.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|Operacja sesji zabezpieczeń została ukończona pomyślnie po stronie klienta.|  
|SAMLActionNameRequiredOnRead|Ciąg, który jest odczytywany w elemencie SamlAction brakuje lub jego długość wynosi 0.|  
|KerberosMultilegsNotSupported|Tożsamość jest określana jako głównej nazwy użytkownika. Uwierzytelnianie w usłudze działającej na koncie użytkownika wymaga wielu etapy protokołu Kerberos, co jest nieobsługiwane.|  
|SAMLAssertionIdRequired|"Identyfikator potwierdzenia" dla elementu SamlAssertion nie może być zerowa ani pusta.|  
|InvalidOperationForWriterState|Określona operacja jest nieprawidłowa w określonym stanie XmlWriter.|  
|CannotValidateSecurityTokenType|Wystawca uwierzytelnienia tokenu zabezpieczeń określonej nie można sprawdzić poprawności tokenu określonego typu.|  
|X509FindValueMismatch|Określony X509FindType wymaga, aby typ findValue argument być określona wartość. Argument findValue jest innego typu.|  
|TraceCodeSecurityClientSessionCloseSent|Sesja zabezpieczeń klienta wysłała komunikat o zamykaniu.|  
|SuiteDoesNotAcceptAlgorithm|Określony algorytm nie jest akceptowana dla określonej operacji przez pakiet algorytmów określony|  
|TraceCodeSecuritySessionRequestorOperationFailure|Operacja sesji zabezpieczeń klienta nie powiodła się.|  
|SAMLUnableToLoadStatement|Nie można załadować instrukcję SamlStatement.|  
|InnerReaderMustBeAtElement|Wewnętrzny czytnik musi być zawarty w elemencie.|  
|UnableToCreateTokenReference|Nie można utworzyć odwołania do tokenu zabezpieczeń.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Protokół zabezpieczeń zweryfikował komunikat przychodzący.|  
|ObjectIsReadOnly|Obiekt jest tylko do odczytu.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|Sesja zabezpieczeń klienta odrzuciła poprzedni klucz sesji.|  
|SAMLTokenTimeInvalid|SamlToken nie jest czas prawidłowe. Bieżący czas jest poza czasem aktywacji i ważności tokenu.|  
|TraceCodeSecurityIdentityVerificationSuccess|Weryfikacja tożsamości zakończyło się pomyślnie.|  
|SigningTokenHasNoKeys|Określony token podpisujący nie ma kluczy.|  
|TraceCodeSecurityIdentityVerificationFailure|Nie można zweryfikować tożsamości.|  
|AESCryptImportKeyFailed|Nie można zaimportować materiału klucza.|  
|FailInitializeSecurityContext|Nie można wykonać funkcji InitializeSecurityContent. Upewnij się, że główna nazwa usługi jest poprawny.|  
|TraceCodeStreamSecurityUpgradeAccepted|Uaktualnienie zabezpieczeń strumienia zostało pomyślnie przyjęte.|  
|SAMLAuthorityBindingRequiresLocation|Atrybut "Lokalizacja", który został określony na SamlAuthorityBinding nie może być zerowy lub jego długość wynosi 0.|  
|PublicKeyNotDSA|Klucz publiczny nie jest kluczem DSA.|  
|ImpersonationLevelNotSupported|Tryby uwierzytelniania przy użyciu protokołu Kerberos nie obsługuje poziomu personifikacji określony. Określ prawidłowy poziom identyfikację lub personifikację.|  
|RequiredTargetNotSigned|Element o określonym identyfikatorze jest wymagany do podpisana, ale nie jest.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|Atrybut "AuthenticationInstant" odczytywanego elementu SamlAuthenticationStatement lub jego długość wynosi 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|SamlEvidence odczytywane nie zawiera odwołania do lub osadzonego elementu SamlAssertion.|  
|LengthOfArrayToConvertMustGreaterThanZero|Długość tablicy można przekonwertować na liczbę całkowitą musi być większa niż 0.|  
|InvalidAsyncResult|Nieprawidłowy element AsyncResult.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|Metoda IssuanceTokenProvider usunęła wygasły token usługi.|  
|IncorrectUserNameFormat|Nazwa użytkownika jest w nieprawidłowym formacie. Format nazwy użytkownika musi być w formie "Nazwa użytkownika" lub "domeny\\\username".|  
|TraceCodeExportSecurityChannelBindingEntry|Uruchamianie metody zabezpieczeń ExportChannelBinding.|  
|UnsupportedInputTypeForTransform|Określony typ danych wejściowych nie jest obsługiwana dla transformacji.|  
|CannotFindDocumentRoot|Nie można odnaleźć głównego dokumentu.|  
|XmlBufferQuotaExceeded|Rozmiar wymagany do buforowania zawartości XML przekroczył limit przydziału buforu.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Wystąpił błąd podczas wysyłania odpowiedzi zamknięcia sesji zabezpieczeń do klienta.|  
|UnableToResolveReferenceInSamlSignature|Nie można rozpoznać określonego odwołania w podpisie SAML z identyfikator potwierdzenia.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|SamlSubject wymaga określenia "NameIdentifier" lub atrybutu "ConfirmationMethod". Brakowało jednocześnie.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|"Namespace" brakuje elementu SamlAttribute lub jego długość wynosi 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Nie można odnaleźć atrybutu "ConfirmationMethod" elementu odczytu.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|Wymóg tokenu ma nieoczekiwany typ dla określonej właściwości. Typ właściwości oczekiwany jest inną wartość.|  
|TraceCodeNegotiationTokenProviderAttached|Podłączono element NegotiationTokenProvider.|  
|TraceCodeSpnegoClientNegotiationCompleted|Dostawca tokenów SpnegoTokenProvider zakończył negocjowanie SSPI.|  
|SAMLUnableToLoadUnknownElement|Wybrany element SamlSerializer nie można rozszeregować elementu. Zarejestruj niestandardowy element SamlSerializer do deserializacji niestandardowych elementów.|  
|CreateSequenceRefused|Żądanie utworzenia sekwencji zostało odrzucone przez punkt końcowy RM Destination.|  
|TraceCodeSecuritySessionRedirectApplied|Sesja zabezpieczeń klienta została przekierowana.|  
|SecurityTokenRequirementDoesNotContainProperty|Wymóg tokenu nie zawiera określonej właściwości.|  
|SAMLAttributeValueCannotBeNull|Jeden z atrybutów znaleziona w elemencie SamlAttribute znaleziono wartość null. Upewnij się, że listy nie mają wartość null, podczas tworzenia elementu SamlAttribute.|  
|ValueMustBeGreaterThanZero|Wartość tego argumentu musi być większa niż 0.|  
|TraceCodeNegotiationAuthenticatorAttached|Podłączono element NegotiationTokenAuthenticator.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Element SamlAuthorizationDecisionStatement musi mieć co najmniej jeden element SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Zamknięto wystawcę uwierzytelnienia tokenów zabezpieczających.|  
|TraceCodeSecurityAuditWrittenSuccess|Dziennik inspekcji zabezpieczeń został pomyślnie zapisany.|  
|PrivateKeyNotDSA|Klucz prywatny nie jest kluczem DSA.|  
|MessageNumberRollover|Maksymalna liczba sekwencji dla tej sekwencji została przekroczona.|  
|AESPaddingModeNotSupported|Określony tryb uzupełniania jest nieobsługiwana. Obsługiwane jest tylko PKCS7 i ISO10126.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Wymagane NameIdentifier i elementy atrybutu "ConfirmationMethod" nie został znaleziony dla odczytywanego elementu SamlSubject.|  
|TraceCodeSecurityAuditWrittenFailure|Wystąpił błąd podczas zapisywania w dzienniku inspekcji zabezpieczeń.|  
|UnsupportedCryptoAlgorithm|Określony algorytm kryptograficzny jest nieobsługiwany w tym kontekście.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|Token podpisujący nie ma klucza obsługującego pakiet algorytmów określony.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|Brak ciągu "Identyfikatora" dla elementu SamlNameIdentifier.|  
|SAMLSubjectStatementRequiresSubject|Instrukcja podmiotu SAML wymaga podmiotu SAML, można określić.|  
|TraceCodeSslClientCertMissing|Zdalny klient usługi SSL nie mógł podać wymaganego certyfikatu.|  
|SAMLTokenVersionNotSupported|Określona wersja główna i pomocnicza wersji nie są obsługiwane.|  
|TraceCodeConfigurationIsReadOnly|Konfiguracja jest tylko do odczytu.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Wystąpił błąd podczas wysyłania błędu odnawiania klucza sesji zabezpieczeń do klienta.|  
|TraceCodeSecurityInactiveSessionFaulted|Nieaktywna sesja zabezpieczeń została przerwana przez serwer.|  
|SAMLUnableToLoadAttribute|Nie można załadować elementu SamlAttribute.|  
|Psha1KeyLengthInvalid|Określona długość klucza PSHA1: jest nieprawidłowy.|  
|KeyIdentifierCannotCreateKey|Ten identyfikator SecurityKeyIdentifier nie zawiera klauzuli można utworzyć klucza.|  
|X509IsInUntrustedStore|Określony certyfikat X.509 znajduje się w magazynie certyfikatów niezaufanych.|  
|UnexpectedXmlChildNode|Określony węzeł podrzędny XML określonego typu jest nieoczekiwany dla określonego elementu.|  
|TokenDoesNotMeetKeySizeRequirements|Wymagania dotyczące rozmiaru klucza dla zestawu określony algorytm nie są spełnione przez określony token.|  
|TraceCodeSecuritySessionRequestorStartOperation|Operacja sesji zabezpieczeń została uruchomiona po stronie klienta.|  
|InvalidHexString|Nieprawidłowy format ciągu szesnastkowego.|  
|SamlAttributeClaimResourceShouldBeAString|Konstruktor elementu SamlAttribute wymaga zasób żądania typu 'string'.|  
|SamlSigningTokenNotFound|Element SamlAssertion jest podpisany, ale nie można odnaleźć elementu SamlAssertion tokenu. Upewnij się, że element SecurityTokenResolver zawiera token elementu SamlAssertion.|  
|TraceCodeSecuritySpnToSidMappingFailure|Nie można zamapować ServicePrincipalName do elementu SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Nie można utworzyć elementu formatującego podpis dla określony algorytm z określonym asymetrycznej.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Sesja zabezpieczeń serwera wysłała błąd zamkniętej sesji do klienta.|  
|UnableToFindPrefix|Nie można odnaleźć prefiksu dla określonego prefiksu widoczny używanych na określony element.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Otwarto wystawcę uwierzytelnienia tokenów zabezpieczających.|  
|RequiredAttributeMissing|Określony atrybut jest wymagany dla określonego elementu.|  
|LocalIdCannotBeEmpty|Identyfikator lokalny nie może być pusta. Określ prawidłowy identyfikator "lokalny".|  
|ValueMustBeInRange|Wartość tego argumentu musi należeć do określonego zakresu.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|Metoda IssuanceTokenProvider rozpocząć nową negocjację zabezpieczeń.|  
|InvalidNtMapping|Określony certyfikat X.509 nie można zamapować na konto systemu Windows. Alternatywna nazwa podmiotu głównej nazwy użytkownika jest wymagana.|  
|AESCryptSetKeyParamFailed|Nie można ustawić parametru określonego klucza.|  
|TraceCodeSecuritySessionClosedResponseReceived|Sesja zabezpieczeń klienta otrzymała zamkniętego odpowiedzi z serwera.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Nie można utworzyć deformatera podpisu dla określony algorytm z określonym asymetrycznej.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Asynchroniczne wywołanie zwrotne wywołało wyjątek.|  
|LengthMustBeGreaterThanZero|Długość tego argumentu musi być większa niż 0.|  
|FoundMultipleCerts|Znaleziono wiele certyfikatów X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue. Podaj dokładniejszą wartość wyszukiwania.|  
|AtLeastOneTransformRequired|Element przekształceń musi zawierać co najmniej jedno przekształcenie.|  
|SAMLTokenNotSerialized|Nie można serializować elementu SamlAssertion do pliku XML. Zobacz wyjątek wewnętrzny, aby uzyskać szczegółowe informacje.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Protokół zabezpieczeń zabezpieczył komunikat wychodzący.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Ten element SecurityKeyIdentifierClause nie obsługuje tworzenia klucza.|  
|UnableToResolveTokenReference|Program rozpoznawania nazw tokenów nie może rozpoznać określonego odwołania do tokenu.|  
|UnsupportedEncryptionAlgorithm|Określony algorytm szyfrowania nie jest obsługiwane.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|Element SamlSerializer nie zawiera elementu SecurityTokenSerializer zdolnego do serializacji danego identyfikatora SecurityKeyIdentifier. Jeśli używasz niestandardowego identyfikatora SecurityKeyIdentifier należy podać niestandardowy element SecurityTokenSerializer.|  
|SAMLAttributeShouldHaveOneValue|Nie znaleziono żadnych wartości atrybutów. Atrybut SamlAttribute musi mieć wartość co najmniej jeden atrybut.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Protokół zabezpieczeń nie może zweryfikować komunikatu przychodzącego.|  
|SamlSigningTokenMissing|Element SamlAssertion przekazany do elementu SamlSecurityTokenAuthenticator nie zawiera tokenu podpisującego.|  
|NoPrivateKeyAvailable|Żaden klucz prywatny nie jest dostępna.|  
|ValueMustBeOne|Wartość tego argumentu musi być równa 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Oczekująca sesja zabezpieczeń została uaktywniona przez serwer.|  
|TraceCodeImportSecurityChannelBindingExit|Zakończono metodę zabezpieczeń ImportChannelBinding.|  
|X509CertStoreLocationNotValid|StoreLocation musi być LocalMachine lub CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Ustawienia modułu zapisującego mogą modyfikować tylko wtedy, gdy moduł zapisujący jest w stanie początkowym.|  
|ArgumentInvalidCertificate|Certyfikat jest nieprawidłowy.|  
|DigestVerificationFailedForReference|Podane odwołanie nie można zweryfikować skrótu.|  
|SAMLAuthorityBindingRequiresBinding|Atrybut "Binding" określony w SamlAuthorityBinding nie może być zerowy lub jego długość wynosi 0.|  
|AESInsufficientOutputBuffer|Bufor wyjściowy musi być większa niż określona bajtów.|  
|SAMLAuthorityBindingMissingBindingOnRead|Powiązanie atrybutu brakuje elementu SamlAuthorityBinding lub jego długość wynosi 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|Elementu SamlAuthorityBinding ma nieprawidłowy atrybut AuthorityKind. Format atrybutu AuthorityKind musi mieć postać QName.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|Element NetworkCredentials dostarczony dla tokenu Kerberos nie ma prawidłowej nazwy użytkownika.|  
|SSPIPackageNotSupported|Określony pakiet SSPI nie jest obsługiwany.|  
|TokenCancellationNotSupported|Określony dostawca tokenu nie obsługuje token anulowania.|  
|UnboundPrefixInQName|Określona nazwa kwalifikowana służy niezwiązanego prefiksu.|  
|SAMLAuthorizationDecisionResourceRequired|Określone SamlAuthorizationDecisionStatement "resource" nie może być zerowy lub jego długość wynosi 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Błąd przetwarzania negocjacji zabezpieczeń usługi.|  
|SAMLAssertionIssuerRequired|"Wystawca" określony dla elementu SamlAssertion nie może być zerowa ani pusta.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Nie można utworzyć HashAlgorithm dla określony algorytm z określonym asymetrycznej.|  
|SamlUnableToExtractSubjectKey|Nie można rozpoznać identyfikatora SecurityKeyIdentifier, który został znaleziony w elemencie SamlSubject obiektu SecurityToken. Element SecurityTokenResolver musi zawierać SecurityToken, która jest rozpoznawana jako identyfikator SecurityKeyIdentifier.|  
|ChildNodeTypeMissing|Określony element XML nie ma elementu podrzędnego określonego typu.|  
|TraceCodeSecurityPendingServerSessionClosed|Oczekująca sesja zabezpieczeń została zamknięta przez serwer.|  
|TraceCodeSecuritySessionCloseResponseSent|Sesja zabezpieczeń serwera wysłała do klienta odpowiedź o zamknięciu.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Nie można znormalizować pozycji HostName część adresu punktu końcowego.|  
|FailAcceptSecurityContext|Działanie funkcji AcceptSecurityContext nie powiodło się.|  
|EmptyXmlElementError|Określony element nie może być pusta.|  
|PrefixNotDefinedForNamespace|Prefiks dla określonego obszaru nazw nie jest zdefiniowany w tym kontekście i nie można zadeklarować.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|Elementu SamlAuthorizationDecisionStatement odnaleziono więcej niż jeden dowód. Jest to niedozwolone.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|Elementu SamlSecurityTokenAuthenticator może przetwarzać tylko SamlSecurityTokens. Określony SecurityTokenType została odebrana.|  
|SAMLAttributeStatementMissingAttributeOnRead|Odczytywany element SamlAttributeStatement nie zawiera żadnych elementów "SamlAttribute". Jest to niedozwolone.|  
|CouldNotFindNamespaceForPrefix|Nie można odszukać przestrzeń nazw dla określonego prefiksu.|  
|TraceCodeExportSecurityChannelBindingExit|PIONOWO zwraca metody zabezpieczeń Zakończono ExportChannelBinding!.|  
|AESCryptDecryptFailed|Nie można odszyfrować określonych danych.|  
|SAMLAttributeNamespaceAttributeRequired|"Namespace" określony dla elementu SamlAttribute nie może być zerowy lub jego długość wynosi 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator zakończył negocjowanie SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Sesja zabezpieczeń serwera wysłała błąd odnowienia klucza do klienta.|  
|AlgorithmMismatchForTransform|Wystąpiła niezgodność w algorytmie przekształcania.|  
|UserNameAuthenticationFailed|Uwierzytelnianie przy użyciu mechanizmu określonej nazwy użytkownika i hasła nie powiodło się. Użytkownik nie jest uwierzytelniony.|  
|SamlInvalidSigningToken|Element SamlAssertion została podpisana tokenem, która nie została sprawdzona, zgodnie z protokołu. Jeśli używane są certyfikaty X.509, sprawdź Twojej semantykę sprawdzania poprawności.|  
|TraceCodeSecurityServerSessionKeyUpdated|Klucz sesji zabezpieczeń został zaktualizowany przez serwer.|  
|TraceCodeSecurityServerSessionCloseReceived|Sesja zabezpieczeń serwera odebrała komunikat o zamykaniu od klienta.|  
|SAMLAuthenticationStatementMissingSubject|Brak wymaganego Element SamlSubjectStatement SamlAuthenticationStatement.|  
|UnexpectedEndOfFile|Nieoczekiwany koniec pliku.|  
|UnsupportedAlgorithmForCryptoOperation|Określony algorytm nie jest obsługiwane dla określonej operacji.|  
|XmlLangAttributeMissing|Brak atrybutu XML: lang wymagane.|  
|TraceCodeSecurityImpersonationSuccess|Personifikacja zabezpieczeń zakończyło się pomyślnie na serwerze.|  
|SAMLAuthorityBindingMissingLocationOnRead|Brak elementu SamlAuthorityBinding lub jego długość 0 atrybutu "Location".|  
|SAMLAttributeStatementMissingSubjectOnRead|Brak elementu "SamlSubject" dla SamlAttributeStatement.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Brak elementu "SamlSubject" dla elementu SamlAuthorizationDecisionStatement.|  
|SAMLBadSchema|Podczas odczytywania elementu SamlAssertion tego określonego elementu stwierdzono nie są zgodne ze schematem.|  
|SAMLAssertionIDIsInvalid|Określony "identyfikator potwierdzenia" dla elementu SamlAssertion musi rozpoczynać się od litery lub "_".|  
|TraceCodeSecurityActiveServerSessionRemoved|Aktywna sesja zabezpieczeń została usunięta przez serwer.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Nie można utworzyć elementu keyedHashAlgorithm dla określony algorytm z określonym asymetrycznej.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|"AuthenticationMethod" określony dla elementu SamlAuthenticationStatement nie może być zerowy lub jego długość wynosi 0.|  
|TraceCodeSecurityImpersonationFailure|Personifikacja zabezpieczeń nie powiodła się na serwerze.|  
|Domyślny|(Domyślnie)|  
|UnsupportedNodeTypeInReader|Typ określony węzeł o określonej nazwie nie jest obsługiwany.|
