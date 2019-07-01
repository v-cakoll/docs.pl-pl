---
title: Wyjątki modelu IdentityModel
ms.date: 03/30/2017
ms.assetid: 4ef34497-8ff5-4621-b773-7731cc721231
ms.openlocfilehash: 4b8af2620b6179ce4cff59d7f9871377f06ffe5f
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486667"
---
# <a name="identitymodel-exceptions"></a>Wyjątki modelu IdentityModel
Ten temat zawiera listę wszystkich wyjątków generowanych przez modelu IdentityModel.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Bieżący ciąg|  
|-------------------|--------------------|  
|ValueMustBeOf2Types|Wartość tego argumentu musi być jedną z tych dwóch typów.|  
|SAMLSubjectNameIdentifierRequiresNameValue|Atrybut "Name" określona dla elementu SamlNameIdentifier nie może być wartość null lub jest długość 0.|  
|TraceCodeIssuanceTokenProviderEndSecurityNegotiation|Metoda IssuanceTokenProvider Ukończono negocjowanie zabezpieczeń.|  
|TraceCodeSecurityNewServerSessionKeyIssued|W nowej sesji zabezpieczeń klucz został wystawiony przez serwer.|  
|SAMLAttributeMissingNameAttributeOnRead|Brak "Name" SamlAttribute odczytywanych lub ma on długość 0.|  
|UnknownICryptoType|Implementacja interfejsu ICrypto nie jest obsługiwane.|  
|TraceCodeSecurityTokenProviderClosed|Dostawcy tokenów zabezpieczeń zostało zamknięte.|  
|SAMLUnableToLoadAdvice|Nie można załadować \<saml:advice > element.|  
|SAMLAuthenticationStatementMissingAuthenticationMethodOnRead|Atrybut "AuthenticationMethod" odczytywanego elementu SamlAuthenticationStatement lub jego długość 0.|  
|UnsupportedTransformAlgorithm|Nieobsługiwany algorytm Przekształć lub kanoniczną.|  
|SAMLAudienceRestrictionShouldHaveOneAudience|Obiekt SamlAudienceRestrictionCondition musi zawierać co najmniej jednej grupy odbiorców (URI).|  
|SAMLEvidenceShouldHaveOneAssertion|SamlEvidence musi odwoływać się do co najmniej jeden element SamlAssertion za pomocą identyfikatora lub odwołania.|  
|SAMLAudienceRestrictionInvalidAudienceValueOnRead|Obiekt SamlAudienceRestrictionCondition brakuje wartości w elemencie "Audience".|  
|X509ChainBuildFail|Określone tworzenie łańcucha certyfikatów X.509 nie powiodło się. Certyfikat, który został użyty ma łańcuch zaufania, którego nie można zweryfikować. Zastąp certyfikat lub zmień tryb certificateValidationMode.|  
|XDCannotFindValueInDictionaryString|Identyfikator określonej wartości w ciągu słownika nie znaleziono.|  
|TraceCodeImportSecurityChannelBindingEntry|Uruchamianie metody zabezpieczeń ImportChannelBinding.|  
|PrivateKeyExchangeNotSupported|Klucz prywatny nie obsługuje parametr KeySpec wymiany.|  
|TokenProviderUnableToGetToken|Określonego dostawcy tokenu nie mógł zapewnić tokenu zabezpieczającego.|  
|SAMLEntityCannotBeNullOrEmpty|Określonej jednostki elementu SamlAssertion nie może być zerowa lub pusta.|  
|SAMLAssertionRequireOneStatement|Element SamlAssertion wymaga co najmniej jedną instrukcję. Upewnij się, że dodano co najmniej jeden element SamlStatement tworzonego elementu SamlAssertion.|  
|AESInvalidInputBlockSize|Rozmiar danych wejściowych musi być wielokrotnością liczby bajtów określonej.|  
|AESCryptAcquireContextFailed|Nie można pobrać kontekstu CSP.|  
|SAMLAssertionRequireOneStatementOnRead|Odczytywany element SamlAssertion nie zawiera żadnych elementu SamlStatement. Element SamlAssertion musi zawierać co najmniej jeden element SamlStatement.|  
|TraceCodeSecuritySessionClosedFaultReceived|Sesja zabezpieczeń klienta odebrał błąd zamkniętej sesji z serwera.|  
|TraceCodeIssuanceTokenProviderRedirectApplied|Metoda IssuanceTokenProvider zastosowany nagłówek przekierowania.|  
|TraceCodeSecuritySessionClosedFaultSendFailure|Wystąpił błąd podczas wysyłania sesji zabezpieczeń zamknięte błędów do klienta.|  
|ValueMustBeZero|Wartość tego argumentu musi być 0.|  
|SAMLUnableToResolveSignatureKey|Nie można rozpoznać identyfikatora SecurityKeyIdentifier znalezionego w podpisie elementu SamlAssertion. Nie można zweryfikować podpisu elementu SamlAssertion określonych wystawcy.|  
|X509IsNotInTrustedStore|Określonego certyfikatu X.509, nie znajduje się w magazynie zaufanych osób.|  
|SAMLElementNotRecognized|Określony element nie jest obsługiwana.|  
|SAMLAuthorizationDecisionStatementMissingResourceAttributeOnRead|Atrybutu "Resource" brakuje elementu SamlAuthorizationDecisionStatement lub jego długość 0.|  
|SamlTokenMissingSignature|Element SamlAssertion nie jest podpisany. Element SamlAssertion może być podpisana, ustawiając element SigningCredentials.|  
|ExpectedElementMissing|Brak oczekiwanego elementu z określonych przestrzeni nazw.|  
|NoKeyIdentifierClauseFound|Nie klauzuli określonego typu został znaleziony w elemencie SecurityKeyIdentifier.|  
|MissingPrivateKey|Klucz prywatny nie jest obecne w certyfikacie X.509.|  
|UnexpectedEOFFromReader|Nieoczekiwany koniec pliku z odczytującego XML.|  
|UnsupportedKeyDerivationAlgorithm|Algorytm wyprowadzania klucza określonego nie jest obsługiwany.|  
|TokenDoesNotSupportKeyIdentifierClauseCreation|Określony token nie obsługuje tworzenia klauzuli identyfikatora klucza określonego.|  
|LastMessageNumberExceeded|Wykryto naruszenie protokołu liczby sekwencji.|  
|SymmetricKeyLengthTooShort|Długość określonego klucza symetrycznego jest za krótkie.|  
|SAMLAuthorityBindingMissingAuthorityKindOnRead|Odczytywany element SamlAuthorityBinding zawiera atrybut "AuthorityKind", którego brakowało lub długość 0.  Jest to niedozwolone.|  
|XmlTokenBufferIsEmpty|Element XmlTokenBuffer jest pusty.|  
|InvalidXmlQualifiedName|Oczekiwano kwalifikowanej nazwy Xml, ale znaleziono nieprawidłową nazwę.|  
|SAMLAuthorityKindMissingName|Przez nazwę XmlQualifiedName, który reprezentuje "AuthorityKind" w SamlAuthorityBinding nie może być wartość null lub jest długość 0.|  
|AESCryptEncryptFailed|Nie można zaszyfrować określonych danych.|  
|AuthorizationContextCreated|Kontekst autoryzacji o określonym identyfikatorze jest tworzony.|  
|SamlSerializerUnableToReadSecurityKeyIdentifier|Element SamlSerializer nie zawiera elementu SecurityTokenSerializer odczytywania identyfikatora SecurityKeyIdentifier. Jeśli używasz niestandardowego elementu SecurityKeyIdentifier, musisz podać niestandardowy element SecurityTokenSerializer.|  
|TraceCodeIssuanceTokenProviderServiceTokenCacheFull|Metoda IssuanceTokenProvider zmniejszona pamięci podręcznej tokenu usługi.|  
|TraceCodeSecurityTokenProviderOpened|Dostawcy tokenów zabezpieczeń został otwarty.|  
|PublicKeyNotRSA|Klucz publiczny nie jest kluczem RSA.|  
|InvalidReaderState|Określony stan jest nieprawidłowy dla podany czytnik danych wejściowych.|  
|UnableToResolveReferenceUriForSignature|Nie można rozpoznać określonego identyfikatora URI w podpisie do obliczania skrótu.|  
|EmptyBase64Attribute|Znaleziono pustą wartość base64 wymaganego atrybutu nazwy i przestrzeni nazw.|  
|SAMLSubjectRequiresConfirmationMethodWhenConfirmationDataOrKeyInfoIsSpecified|SAML SubjectConfirmation wymaga metody potwierdzenia, jeśli nie określono danych potwierdzenia lub KeyInfo.|  
|SAMLAudienceRestrictionShouldHaveOneAudienceOnRead|Obiekt SamlAudienceRestrictionCondition musi zawierać wartość co najmniej jeden "Audience". Nie znaleziono żadnych.|  
|TokenProviderUnableToRenewToken|Określonego dostawcy tokenu nie mógł odnowić tokenu zabezpieczającego.|  
|AESIVLengthNotSupported|IV określonej usługi bits nie jest obsługiwane. Obsługiwane jest tylko IV 128 bitów.|  
|SAMLAuthorityBindingMissingAuthorityKind|Element SamlAuthorityBinding musi zawierać atrybut "AuthorityKind", nie ma wartości null.|  
|TraceCodeSecuritySessionDemuxFailure|Przychodząca wiadomość nie jest częścią istniejącej sesji zabezpieczeń.|  
|TokenRenewalNotSupported|Określonego dostawcy tokenu nie obsługuje odnowienia tokenu.|  
|AtLeastOneReferenceRequired|Co najmniej jedno odwołanie jest wymagany w podpisie.|  
|SAMLSignatureAlreadyRead|Podpis został już odczytany w potwierdzenie SAML.|  
|AlgorithmAndPrivateKeyMisMatch|Określony algorytm i klucz prywatny nie są zgodne.|  
|EmptyTransformChainNotSupported|Pusty łańcuch przekształcenia nie jest obsługiwane.|  
|SspiWrapperEncryptDecryptAssert1|SSPIWrapper::EncryptDecryptHelper&#124;'offset' is out of range.|  
|SspiWrapperEncryptDecryptAssert2|SSPIWrapper::EncryptDecryptHelper&#124;"size" jest poza zakresem. SecurityTokenManagerCannotCreateAuthenticatorForRequirement = bezpieczeństwo Menedżer tokenów nie może utworzyć wystawcy uwierzytelnienia tokenu dla konkretnego wymagania.|  
|UnableToCreateKeyedHashAlgorithm|Nie można utworzyć elementu KeyedHashAlgorithm od określonej wartości dla algorytmu określonej sygnatury.|  
|SAMLUnableToLoadAssertion|\<SAML: Assertion > nie można załadować elementu.|  
|X509FindValueMismatchMulti|Określone X509FindType wymaga, aby typ findValue argumentu, aby mieć jedną z wartości 2. Argument findValue jest innego typu.|  
|TraceCodeSecurityIdentityDeterminationSuccess|EndpointAddress został określić tożsamości.|  
|UndefinedUseOfPrefixAtElement|Nie ma określonego prefiksu, który jest używany w elemencie obszaru nazw zdefiniowane.|  
|TraceCodeSecuritySessionResponderOperationFailure|Operacja sesji zabezpieczeń nie powiodło się na serwerze.|  
|CannotFindCert|Nie można odnaleźć certyfikatu X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName , StoreLocation, FindType, FindValue.|  
|X509InvalidUsageTime|Określony czas użycia certyfikatu X.509 jest nieprawidłowy. Czas użycia nie przypada między wymaganymi czasami notbefore i notafter.|  
|TraceCodeSecurityIdentityDeterminationFailure|Nie można określić tożsamości EndpointAddress.|  
|AsyncObjectAlreadyEnded|End — Metoda została już wywołana dla tego obiektu wynik asynchroniczny.|  
|ExternalDictionaryDoesNotContainAllRequiredStrings|Słownik zewnętrznych nie zawiera definicji dla wszystkich wymaganych parametrów. Określony ciąg nie jest dostępna w słowniku zdalnym.|  
|TraceCodeSecuritySessionKeyRenewalFaultReceived|Sesja zabezpieczeń klienta odebrał błąd odnowienia klucza z serwera.|  
|SAMLActionNameRequired|Ciąg, który reprezentuje SamlAction nie może być wartość null lub jest długość 0.|  
|SignatureVerificationFailed|Nie można zweryfikować podpisu.|  
|TraceCodeSecurityContextTokenCacheFull|Element SecurityContextSecurityToken pamięć podręczna jest pełna.|  
|SAMLAssertionMissingMajorVersionAttributeOnRead|Brak elementu MajorVersion dla odczytywanego elementu SamlAssertion nie istnieje lub ma on długość 0.|  
|SamlAttributeClaimRightShouldBePossessProperty|Ten konstruktor SamlAttribute wymaga, że prawo żądania ma wartość system.IdentityModel.Claims.Rights.PossessProperty.|  
|AuthorizationPolicyEvaluated|Oceny zasad o określonym identyfikatorze.|  
|SAMLUnableToLoadCondtions<!-- the misspelling here is deliberate. -->|\<SAML: conditions > nie można załadować elementu.|  
|AESKeyLengthNotSupported|Klucz określonego usługi bits nie jest obsługiwany. Tylko 128, 192- i 256 klucz usługi bits jest obsługiwany.|  
|UserNameCannotBeEmpty|Nazwa użytkownika nie może być pusta.|  
|AlgorithmAndPublicKeyMisMatch|Określony algorytm i klucz publiczny nie są zgodne.|  
|SAMLUnableToLoadCondtion<!-- the misspelling here is deliberate. -->|\<SAML: conditions > nie można załadować elementu.|  
|SamlAssertionMissingSigningCredentials|Nie ustawiono elementu SigningCredentials w elemencie SamlAssertion. Element SamlAssertion musi być podpisany, ustaw prawidłowy element SigningCredentials w elemencie SamlAssertion, aby kontynuować.|  
|SspiPayloadNotEncrypted|Dane binarne nie została zaszyfrowana za pomocą kontekstu zabezpieczeń SSPI.|  
|SAMLAuthorizationDecisionShouldHaveOneActionOnRead|SamlAuthorizationDecisionStatement, który jest odczytywany nie zawiera żadnych SamlAction.|  
|TraceCodeSecurityBindingSecureOutgoingMessageFailure|Protokół zabezpieczeń nie można zabezpieczyć komunikatu wychodzącego.|  
|UndefinedUseOfPrefixAtAttribute|Nie ma określonego prefiksu na określony atrybut obszaru nazw zdefiniowane.|  
|NoInputIsSetForCanonicalization|Nie ustawiono wejścia do zapisywania danych wyjściowych w postaci kanonicznej.|  
|TraceCodeSecurityPendingServerSessionAdded|Oczekująca sesja zabezpieczeń jest dodawany do serwera.|  
|AsyncCallbackException|AsyncCallback zgłosiła wyjątek.|  
|PrivateKeyNotRSA|Klucz prywatny nie jest kluczem RSA.|  
|TraceCodeSecurityClientSessionKeyRenewed|Sesja zabezpieczeń klienta odnowić klucz sesji.|  
|SAMLAuthorizationDecisionStatementMissingDecisionAttributeOnRead|Decyzja brakuje elementu SamlAuthorizationDecisionStatement lub jego długość 0.|  
|SAMLAttributeNameAttributeRequired|Atrybut "Name" określony dla elementu SamlAttribute nie może być wartość null lub jest długość 0.|  
|SamlSerializerRequiresExternalSerializers|Element SamlSerializer wymaga elementu SecurityTokenSerializer SecurityKeyIdentifier występującą w tokenie.|  
|UnableToResolveKeyReference|Program rozpoznawania tokenów nie może rozpoznać odwołania klucza zabezpieczeń.|  
|UnsupportedKeyWrapAlgorithm|Algorytm określonych zawijania klucza nie jest obsługiwany.|  
|SAMLAssertionMissingIssuerAttributeOnRead|Brak "Issuer" dla odczytywanego elementu SamlAssertion lub ma on długość 0.|  
|TraceCodeIssuanceTokenProviderUsingCachedToken|Metoda IssuanceTokenProvider używany token usługi pamięci podręcznej.|  
|AESCryptGetKeyParamFailed|Nie można pobrać określonego parametru klucza.|  
|InvalidNamespaceForEmptyPrefix|Przestrzeń nazw jest nieprawidłowa dla pustego prefiksu.|  
|AESCipherModeNotSupported|Tryb szyfrowania określonego nie jest obsługiwana. Tylko CBC jest obsługiwane.|  
|ArgumentCannotBeEmptyString|Argument musi być niepustym ciągiem.|  
|SAMLAssertionMissingMinorVersionAttributeOnRead|Brak MinorVersion dla odczytywanego elementu SamlAssertion lub ma on długość 0.|  
|SpecifiedStringNotAvailableInDictionary|Określony ciąg nie jest wpis w bieżącym słowniku.|  
|KerberosApReqInvalidOrOutOfMemory|Kerberos jest nieprawidłowy lub system nie ma wystarczającej ilości pamięci.|  
|FailLogonUser|Funkcji LogonUser nie powiodło się dla określonego użytkownika. Upewnij się, że użytkownik ma prawidłowe konto Windows.|  
|ValueMustBeNonNegative|Wartość tego argumentu musi być nieujemna.|  
|X509ValidationFail|Określony walidacji certyfikatu X.509 nie powiodło się.|  
|TraceCodeSecuritySessionRequestorOperationSuccess|Operacja sesji zabezpieczeń została ukończona pomyślnie na kliencie.|  
|SAMLActionNameRequiredOnRead|Ciąg, który jest odczytywany w elemencie SamlAction nie istnieje lub ma on długość 0.|  
|KerberosMultilegsNotSupported|Tożsamość jest określona jako nazwy UPN. Uwierzytelnianie w usłudze działającej na koncie użytkownika wymaga wielu nogi protokołu Kerberos, która nie jest obsługiwana.|  
|SAMLAssertionIdRequired|Element "assertionId" dla elementu SamlAssertion nie może być zerowa lub pusta.|  
|InvalidOperationForWriterState|Określona operacja jest nieprawidłowa w określonym stanie XmlWriter.|  
|CannotValidateSecurityTokenType|Wystawcy uwierzytelniania tokenu zabezpieczeń określone, nie można zweryfikować tokenu określonego typu.|  
|X509FindValueMismatch|Określony X509FindType wymaga, aby typ findValue argument do określonej wartości. Argument findValue jest innego typu.|  
|TraceCodeSecurityClientSessionCloseSent|Zamknij komunikat został wysłany przez klienta sesji zabezpieczeń.|  
|SuiteDoesNotAcceptAlgorithm|Określony algorytm nie jest akceptowana dla określonej operacji przez pakiet algorytmów określonego|  
|TraceCodeSecuritySessionRequestorOperationFailure|Operacja sesji zabezpieczeń klienta nie powiodło się.|  
|SAMLUnableToLoadStatement|Nie można załadować elementu SamlStatement.|  
|InnerReaderMustBeAtElement|Wewnętrzny czytnik musi być zawarty w elemencie.|  
|UnableToCreateTokenReference|Nie można utworzyć odwołania do tokenu zabezpieczającego.|  
|TraceCodeSecurityBindingIncomingMessageVerified|Protokół zabezpieczeń zweryfikować komunikatu przychodzącego.|  
|ObjectIsReadOnly|Obiekt jest tylko do odczytu.|  
|TraceCodeSecurityClientSessionPreviousKeyDiscarded|Sesja zabezpieczeń klienta odrzucone poprzedniego klucza sesji.|  
|SAMLTokenTimeInvalid|SamlToken nie jest czas prawidłowe. Bieżąca godzina jest poza podczas aktywacji i ważności tokenu.|  
|TraceCodeSecurityIdentityVerificationSuccess|Weryfikacja tożsamości zakończyła się pomyślnie.|  
|SigningTokenHasNoKeys|Określony token podpisujący nie ma kluczy.|  
|TraceCodeSecurityIdentityVerificationFailure|Nie można zweryfikować tożsamości.|  
|AESCryptImportKeyFailed|Nie można zaimportować materiał klucza.|  
|FailInitializeSecurityContext|InitializeSecurityContent failed. Upewnij się, że główna nazwa usługi jest poprawny.|  
|TraceCodeStreamSecurityUpgradeAccepted|Uaktualnienie zabezpieczeń strumienia zostało zaakceptowane pomyślnie.|  
|SAMLAuthorityBindingRequiresLocation|Atrybut "Location", który jest określony w SamlAuthorityBinding nie może być wartość null lub jest długość 0.|  
|PublicKeyNotDSA|Klucz publiczny nie jest kluczem DSA.|  
|ImpersonationLevelNotSupported|Tryby uwierzytelniania przy użyciu protokołu Kerberos nie obsługują poziomu personifikacji określony. Określ prawidłowy poziom identyfikację lub personifikację.|  
|RequiredTargetNotSigned|Element o określonym identyfikatorze będzie musiał być podpisana, ale nie zostało.|  
|SAMLAuthenticationStatementMissingAuthenticationInstanceOnRead|Atrybut "AuthenticationInstant" odczytywanego elementu SamlAuthenticationStatement lub jego długość 0.|  
|SAMLEvidenceShouldHaveOneAssertionOnRead|SamlEvidence odczytywanych nie zawiera odwołania do lub osadzonego elementu SamlAssertion.|  
|LengthOfArrayToConvertMustGreaterThanZero|Długość tablicy można przekonwertować na liczbę całkowitą musi być większa niż 0.|  
|InvalidAsyncResult|Nieprawidłowy element AsyncResult.|  
|TraceCodeIssuanceTokenProviderRemovedCachedToken|Metoda IssuanceTokenProvider usunęła wygasły token usługi.|  
|IncorrectUserNameFormat|Nazwa użytkownika jest w nieprawidłowym formacie. Format nazwy użytkownika musi być w formie "Nazwa użytkownika" lub "domena\\\username".|  
|TraceCodeExportSecurityChannelBindingEntry|Uruchamianie metody zabezpieczeń ExportChannelBinding.|  
|UnsupportedInputTypeForTransform|Określony typ danych wejściowych nie jest obsługiwany dla przekształcenia.|  
|CannotFindDocumentRoot|Nie można odnaleźć katalogu głównego dokumentu.|  
|XmlBufferQuotaExceeded|Rozmiar wymagany do buforowania zawartości XML przekroczył limit przydziału buforu.|  
|TraceCodeSecuritySessionClosedResponseSendFailure|Wystąpił błąd podczas wysyłania zabezpieczeń sesji Zamknij odpowiedź do klienta.|  
|UnableToResolveReferenceInSamlSignature|Nie można rozpoznać określonego odwołania w podpisie SAML z identyfikator potwierdzenia.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethod|SamlSubject wymaga określenia "NameIdentifier" lub atrybutu "ConfirmationMethod". Zarówno brakowało.|  
|SAMLAttributeMissingNamespaceAttributeOnRead|"Namespace" Brak SamlAttribute odczytywanych lub jego długość 0.|  
|SAMLSubjectConfirmationClauseMissingConfirmationMethodOnRead|Nie można odnaleźć atrybutu "ConfirmationMethod" elementu odczytywany.|  
|SecurityTokenRequirementHasInvalidTypeForProperty|Wymaganie tokenu ma nieoczekiwany typ dla określonej właściwości. Oczekiwanym typem właściwości jest inna wartość.|  
|TraceCodeNegotiationTokenProviderAttached|Podłączono element NegotiationTokenProvider.|  
|TraceCodeSpnegoClientNegotiationCompleted|Dostawca tokenów SpnegoTokenProvider ukończyć negocjacji interfejsu SSPI.|  
|SAMLUnableToLoadUnknownElement|Wybrany Serializator nie może deserializować tego elementu. Zarejestruj niestandardowy serializator SamlSerializer, aby deserializować elementy niestandardowe.|  
|CreateSequenceRefused|Żądanie utworzenia sekwencji zostało odrzucone przez docelowym Menedżera zasobów.|  
|TraceCodeSecuritySessionRedirectApplied|Sesja zabezpieczeń klienta zostało przekierowane.|  
|SecurityTokenRequirementDoesNotContainProperty|Wymaganie tokenu nie zawiera określonej właściwości.|  
|SAMLAttributeValueCannotBeNull|Jeden z atrybutów znaleziona w elemencie SamlAttribute znaleziono wartość null. Upewnij się, że listy nie mają wartości null, podczas tworzenia elementu SamlAttribute.|  
|ValueMustBeGreaterThanZero|Wartość tego argumentu musi być większa niż 0.|  
|TraceCodeNegotiationAuthenticatorAttached|Podłączono element NegotiationTokenAuthenticator.|  
|ValueMustBePositive||  
|SAMLAuthorizationDecisionShouldHaveOneAction|Element SamlAuthorizationDecisionStatement musi mieć co najmniej jeden element SamlAction.|  
|TraceCodeSecurityTokenAuthenticatorClosed|Wystawcy uwierzytelniania tokenu zabezpieczeń zostało zamknięte.|  
|TraceCodeSecurityAuditWrittenSuccess|Dziennik inspekcji zabezpieczeń został pomyślnie zapisany.|  
|PrivateKeyNotDSA|Klucz prywatny nie jest kluczem DSA.|  
|MessageNumberRollover|Maksymalna liczba sekwencji dla tej sekwencji została przekroczona.|  
|AESPaddingModeNotSupported|Określony tryb uzupełniania nie jest obsługiwana. Tylko PKCS7 i ISO10126 jest obsługiwane.|  
|SAMLSubjectRequiresNameIdentifierOrConfirmationMethodOnRead|Nie ma wymaganych NameIdentifier i elementy atrybutu "ConfirmationMethod" dla odczytywanego elementu SamlSubject.|  
|TraceCodeSecurityAuditWrittenFailure|Wystąpił błąd podczas zapisywania dziennika inspekcji zabezpieczeń.|  
|UnsupportedCryptoAlgorithm|Określony algorytm szyfrowania nie jest obsługiwany w tym kontekście.|  
|SigningTokenHasNoKeysSupportingTheAlgorithmSuite|Token podpisujący nie ma klucza obsługującego pakiet algorytmów określony.|  
|SAMLNameIdentifierMissingIdentifierValueOnRead|Brak ciągu "Identyfikator" dla odczytywanego elementu SamlNameIdentifier.|  
|SAMLSubjectStatementRequiresSubject|Instrukcja podmiotu SAML wymaga podmiotu SAML, można określić.|  
|TraceCodeSslClientCertMissing|Nie można podać wymaganego certyfikatu zdalnego klienta SSL.|  
|SAMLTokenVersionNotSupported|Określonej wersji głównej i pomocniczej wersji nie są obsługiwane.|  
|TraceCodeConfigurationIsReadOnly|Konfiguracja jest tylko do odczytu.|  
|TraceCodeSecuritySessionRenewFaultSendFailure|Wystąpił błąd podczas wysyłania błąd odnowienia na klucz sesji zabezpieczeń do klienta.|  
|TraceCodeSecurityInactiveSessionFaulted|Sesja nieaktywne zabezpieczeń została przerwana przez serwer.|  
|SAMLUnableToLoadAttribute|Nie można załadować elementu SamlAttribute.|  
|Psha1KeyLengthInvalid|Określona długość klucza PSHA1: jest nieprawidłowy.|  
|KeyIdentifierCannotCreateKey|Ten element SecurityKeyIdentifier nie ma żadnej klauzuli, która może utworzyć klucz.|  
|X509IsInUntrustedStore|Określony certyfikat X.509 znajdują się w magazynie certyfikatów niezaufanych.|  
|UnexpectedXmlChildNode|Określony węzeł podrzędny XML określonego typu jest nieoczekiwany dla określonego elementu.|  
|TokenDoesNotMeetKeySizeRequirements|Wymagania dotyczące rozmiaru klucza dla zestawu określony algorytm nie są spełnione przez określony token.|  
|TraceCodeSecuritySessionRequestorStartOperation|Operacja sesji zabezpieczeń została uruchomiona na kliencie.|  
|InvalidHexString|Nieprawidłowy format ciągu szesnastkowego.|  
|SamlAttributeClaimResourceShouldBeAString|Ten konstruktor SamlAttribute wymaga zasób żądania typu "string".|  
|SamlSigningTokenNotFound|Element SamlAssertion jest podpisany, ale nie można odnaleźć tokenu, który podpisał element SamlAssertion. Upewnij się, że element SecurityTokenResolver zawiera token, który podpisał element SamlAssertion.|  
|TraceCodeSecuritySpnToSidMappingFailure|Nie można zamapować ServicePrincipalName do elementu SecurityIdentifier.|  
|UnableToCreateSignatureFormatterFromAsymmetricCrypto|Nie można utworzyć elementu formatującego podpisu dla określonego algorytmu z określonym asymetrycznej.|  
|TraceCodeSecurityServerSessionClosedFaultSent|Sesja zabezpieczeń serwera błąd zamkniętej sesji są wysyłane do klienta.|  
|UnableToFindPrefix|Nie można odnaleźć prefiksu dla określonego prefiksu widoczny używanych na określony element.|  
|TraceCodeSecurityTokenAuthenticatorOpened|Wystawcy uwierzytelniania tokenu zabezpieczeń został otwarty.|  
|RequiredAttributeMissing|Określony atrybut jest wymagany dla określonego elementu.|  
|LocalIdCannotBeEmpty|Identyfikator localId nie może być pusta. Określ prawidłowy identyfikator "localId".|  
|ValueMustBeInRange|Wartość tego argumentu, muszą należeć do zakresu.|  
|TraceCodeIssuanceTokenProviderBeginSecurityNegotiation|Metoda IssuanceTokenProvider uruchomić nowy negocjowanie zabezpieczeń.|  
|InvalidNtMapping|Nie można zamapować określonego certyfikatu X.509 do konta Windows. Alternatywna nazwa podmiotu głównej nazwy użytkownika jest wymagana.|  
|AESCryptSetKeyParamFailed|Nie można ustawić parametru określonego klucza.|  
|TraceCodeSecuritySessionClosedResponseReceived|Sesja zabezpieczeń klienta otrzymała zamknięte odpowiedzi z serwera.|  
|UnableToCreateSignatureDeformatterFromAsymmetricCrypto|Nie można utworzyć deformatera podpisu dla określonego algorytmu z określonym asymetrycznej.|  
|TraceCodeIdentityModelAsyncCallbackThrewException|Asynchroniczne wywołanie zwrotne zgłosiła wyjątek.|  
|LengthMustBeGreaterThanZero|Długość tego argumentu musi być większa niż 0.|  
|FoundMultipleCerts|Znaleziono wiele certyfikatów X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue. Podaj dokładniejszą wartość wyszukiwania.|  
|AtLeastOneTransformRequired|Element przekształcenia musi zawierać co najmniej jedno przekształcenie.|  
|SAMLTokenNotSerialized|Element SamlAssertion nie może być serializowany do XML. Zobacz wyjątek wewnętrzny, aby uzyskać szczegółowe informacje.|  
|TraceCodeSecurityBindingOutgoingMessageSecured|Protokół zabezpieczeń zabezpieczonych wiadomości wychodzących.|  
|KeyIdentifierClauseDoesNotSupportKeyCreation|Ten element SecurityKeyIdentifierClause nie obsługuje tworzenia klucza.|  
|UnableToResolveTokenReference|Program rozpoznawania tokenów nie może rozpoznać określonego odwołania do tokenu.|  
|UnsupportedEncryptionAlgorithm|Określony algorytm szyfrowania nie jest obsługiwane.|  
|SamlSerializerUnableToWriteSecurityKeyIdentifier|Element SamlSerializer nie zawiera elementu SecurityTokenSerializer umożliwiającego serializację danej wartości SecurityKeyIdentifier. Jeśli używasz niestandardowego elementu SecurityKeyIdentifier, musisz podać niestandardowy element SecurityTokenSerializer.|  
|SAMLAttributeShouldHaveOneValue|Nie znaleziono żadnych wartości atrybutu. Atrybut SamlAttribute musi mieć wartość co najmniej jeden atrybut.|  
|TraceCodeSecurityBindingVerifyIncomingMessageFailure|Protokół zabezpieczeń nie można zweryfikować komunikatu przychodzącego.|  
|SamlSigningTokenMissing|Element SamlAssertion przekazany do elementu SamlSecurityTokenAuthenticator nie zawiera token podpisujący.|  
|NoPrivateKeyAvailable|Brak klucza prywatnego jest dostępna.|  
|ValueMustBeOne|Wartość tego argumentu musi wynosić 1.|  
|TraceCodeSecurityPendingServerSessionRemoved|Oczekująca sesja zabezpieczeń zostało aktywowane przez serwer.|  
|TraceCodeImportSecurityChannelBindingExit|Zakończono metodę zabezpieczeń ImportChannelBinding.|  
|X509CertStoreLocationNotValid|StoreLocation musi być LocalMachine lub CurrentUser.|  
|SettingdMayBeModifiedOnlyWhenTheWriterIsInStartState|Ustawienia modułu zapisującego może być modyfikowany tylko wtedy, gdy moduł zapisujący jest w stanie początkowym.|  
|ArgumentInvalidCertificate|Certyfikat jest nieprawidłowy.|  
|DigestVerificationFailedForReference|Nie można zweryfikować skrótu określone odwołanie.|  
|SAMLAuthorityBindingRequiresBinding|Atrybut "Binding" określony w SamlAuthorityBinding nie może być wartość null lub jest długość 0.|  
|AESInsufficientOutputBuffer|Bufor wyjściowy musi być większa niż określona bajtów.|  
|SAMLAuthorityBindingMissingBindingOnRead|"Binding" atrybutu elementu SamlAuthorityBinding nie istnieje lub jego długość 0.|  
|SAMLAuthorityBindingInvalidAuthorityKind|SamlAuthorityBinding odczytywanych ma nieprawidłowy atrybut AuthorityKind. Format atrybutu AuthorityKind musi mieć postać QName.|  
|ProvidedNetworkCredentialsForKerberosHasInvalidUserName|Element NetworkCredentials podany dla tokenu protokołu Kerberos nie ma prawidłowej nazwy użytkownika.|  
|SSPIPackageNotSupported|Określony pakiet SSPI nie jest obsługiwana.|  
|TokenCancellationNotSupported|Określonego dostawcy tokenu nie obsługuje anulowania tokenu.|  
|UnboundPrefixInQName|W określonej nazwie kwalifikowanej jest używany niepowiązany prefiks.|  
|SAMLAuthorizationDecisionResourceRequired|Określony do SamlAuthorizationDecisionStatement "Zasób" nie może być wartość null lub jest długość 0.|  
|TraceCodeSecurityNegotiationProcessingFailure|Błąd przetwarzania negocjacji zabezpieczeń usługi.|  
|SAMLAssertionIssuerRequired|"Issuer" określony dla elementu SamlAssertion nie może być zerowa lub pusta.|  
|UnableToCreateHashAlgorithmFromAsymmetricCrypto|Nie można utworzyć algorytm dla określonego algorytmu z określonym asymetrycznej.|  
|SamlUnableToExtractSubjectKey|Nie można rozpoznać identyfikatora SecurityKeyIdentifier znalezionego w elemencie SamlSubject SecurityToken. Element SecurityTokenResolver musi zawierać SecurityToken, która jest rozpoznawana jako element SecurityKeyIdentifier.|  
|ChildNodeTypeMissing|Określony element XML nie ma elementu podrzędnego określonego typu.|  
|TraceCodeSecurityPendingServerSessionClosed|Sesja oczekujące zabezpieczeń zostało zamknięte przez serwer.|  
|TraceCodeSecuritySessionCloseResponseSent|Sesja zabezpieczeń serwera wysyłane Zamknij odpowiedź do klienta.|  
|TraceCodeSecurityIdentityHostNameNormalizationFailure|Nie można znormalizować HostName część adresu punktu końcowego.|  
|FailAcceptSecurityContext|Działanie funkcji AcceptSecurityContext nie powiodło się.|  
|EmptyXmlElementError|Określony element nie może być pusta.|  
|PrefixNotDefinedForNamespace|Prefiks dla określonego obszaru nazw nie jest zdefiniowany w tym kontekście i nie może być zadeklarowana.|  
|SAMLAuthorizationDecisionHasMoreThanOneEvidence|Elementu SamlAuthorizationDecisionStatement odnaleziono więcej niż jeden dowodów. Jest to niedozwolone.|  
|SamlTokenAuthenticatorCanOnlyProcessSamlTokens|Elementu SamlSecurityTokenAuthenticator może przetwarzać tylko SamlSecurityTokens. Określony SecurityTokenType została odebrana.|  
|SAMLAttributeStatementMissingAttributeOnRead|Odczytywany element SamlAttributeStatement nie zawiera żadnych elementów "SamlAttribute". Jest to niedozwolone.|  
|CouldNotFindNamespaceForPrefix|Nie można wyszukać określonego prefiksu przestrzeni nazw.|  
|TraceCodeExportSecurityChannelBindingExit|PIONOWO zwraca metody zabezpieczeń Zakończono ExportChannelBinding!.|  
|AESCryptDecryptFailed|Nie można odszyfrować określone dane.|  
|SAMLAttributeNamespaceAttributeRequired|"Namespace" określony dla elementu SamlAttribute nie może być wartość null lub jest długość 0.|  
|TraceCodeSpnegoServiceNegotiationCompleted|SpnegoTokenAuthenticator ukończyć negocjacji interfejsu SSPI.|  
|TraceCodeSecurityServerSessionRenewalFaultSent|Sesja zabezpieczeń serwera wysłała błąd odnawiania klucza do klienta.|  
|AlgorithmMismatchForTransform|Wystąpiła niezgodność w algorytmie transformacji.|  
|UserNameAuthenticationFailed|Nie można uwierzytelnić przy użyciu mechanizmu określonej nazwy użytkownika i hasła. Użytkownik nie jest uwierzytelniony.|  
|SamlInvalidSigningToken|Element SamlAssertion jest podpisany przy użyciu tokenu, który nie został zweryfikowany zgodnie z protokołem. Jeśli używasz certyfikatów X.509, sprawdź swoje semantykę sprawdzania poprawności.|  
|TraceCodeSecurityServerSessionKeyUpdated|Klucz sesji zabezpieczeń został zaktualizowany przez serwer.|  
|TraceCodeSecurityServerSessionCloseReceived|Sesja zabezpieczeń serwera odebrano Zamknij komunikat z klienta.|  
|SAMLAuthenticationStatementMissingSubject|Brak wymaganego Element SamlSubjectStatement SamlAuthenticationStatement.|  
|UnexpectedEndOfFile|Nieoczekiwany koniec pliku.|  
|UnsupportedAlgorithmForCryptoOperation|Określony algorytm nie jest obsługiwane dla określonej operacji.|  
|XmlLangAttributeMissing|Brak atrybutu wymagane XML: lang.|  
|TraceCodeSecurityImpersonationSuccess|Personifikacja zabezpieczeń powiodło się na serwerze.|  
|SAMLAuthorityBindingMissingLocationOnRead|"Location" atrybutu elementu SamlAuthorityBinding nie istnieje lub jego długość 0.|  
|SAMLAttributeStatementMissingSubjectOnRead|Brak "SamlSubject" dla SamlAttributeStatement.|  
|SAMLAuthorizationDecisionStatementMissingSubjectOnRead|Brak "SamlSubject" dla elementu SamlAuthorizationDecisionStatement.|  
|SAMLBadSchema|Podczas odczytywania elementu SamlAssertion tego określonego elementu stwierdzono nie są zgodne ze schematem.|  
|SAMLAssertionIDIsInvalid|Określony element "assertionId" dla elementu SamlAssertion musi zaczynać się od litery lub znaku "_".|  
|TraceCodeSecurityActiveServerSessionRemoved|Aktywna sesja zabezpieczeń został usunięty przez serwer.|  
|UnableToCreateKeyedHashAlgorithmFromSymmetricCrypto|Nie można utworzyć keyedHashAlgorithm dla określonego algorytmu z określonym asymetrycznej.|  
|SAMLAuthenticationStatementMissingAuthenticationMethod|"AuthenticationMethod" określony dla elementu SamlAuthenticationStatement nie może być wartość null lub jest długość 0.|  
|TraceCodeSecurityImpersonationFailure|Personifikacja zabezpieczeń nie powiodła się na serwerze.|  
|Domyślny|(Domyślnie)|  
|UnsupportedNodeTypeInReader|Określony typ węzła o podanej nazwie nie jest obsługiwane.|
