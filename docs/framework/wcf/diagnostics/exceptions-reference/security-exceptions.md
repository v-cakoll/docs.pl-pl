---
title: Wyjątki zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: e96c317862867b9e461eb2d13dce6ede5b30cf13
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348245"
---
# <a name="security-exceptions"></a>Wyjątki zabezpieczeń

W tym temacie wymieniono wszystkie wyjątki zabezpieczeń.

## <a name="exception-list"></a>Lista wyjątków

|Kod zasobu|Ciąg zasobu|
|-------------------|---------------------|
|AnonymousLogonsAreNotAllowed|Usługa nie umożliwia anonimowego logowania.|
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Komunikat żądania musi być chroniony. Jest to wymagane przez operację określonego kontraktu. Ochrona musi być podana przez określone powiązanie.|
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Komunikat odpowiedzi musi być chroniony. Jest to wymagane przez operację określonego kontraktu. Ochrona musi być podana przez określone powiązanie.|
|AtMostOnePrimarySignatureInReceiveSecurityHeader|W nagłówku zabezpieczeń dozwolony jest tylko jeden podpis podstawowy.|
|BadContextTokenFaultReason|Token kontekstu zabezpieczeń wygasł lub jest nieprawidłowy. Komunikat nie został przetworzony.|
|BadEncryptionState|EncryptedData lub EncryptedKey jest w nieprawidłowym stanie dla tej operacji.|
|BasicHttpMessageSecurityRequiresCertificate|Powiązanie BasicHttp wymaga, aby wartość BasicHttpBinding. Security. Message. ClientCredentialtype była równoważna z typem poświadczeń BasicHttpMessageCredentialType. Certificate dla bezpiecznych komunikatów. Wybierz pozycję transport lub TransportWithMessageCredential zabezpieczenia dla poświadczeń nazwy użytkownika.|
|BasicTokenCannotBeWrittenWithoutEncryption|Nie można zapisać tokenu podstawowego bez szyfrowania.|
|BindingDoesNotSupportProtectionForRst|Określone powiązanie dla określonego kontraktu jest skonfigurowane przy użyciu SecureConversation, ale w trybie uwierzytelniania nie jest możliwe zapewnienie integralności i poufności informacji wymaganych na potrzeby negocjacji.|
|BindingDoesNotSupportWindowsIdenityForImpersonation|Określona operacja kontraktu wymaga tożsamości systemu Windows w celu automatycznej personifikacji. Tożsamość systemu Windows reprezentująca obiekt wywołujący nie jest dostarczana przez określone powiązanie dla określonego kontraktu.|
|CachedNegotiationStateQuotaReached|Usługa nie może buforować stanu negocjowania, ponieważ została osiągnięta określona pojemność. Ponów żądanie.|
|CacheQuotaReached|Nie można dodać elementu. Określono maksymalny rozmiar pamięci podręcznej.|
|CannotDetermineSPNBasedOnAddress|Klient nie może określić nazwy głównej usługi opartej na tożsamości na określonym adresie docelowym na potrzeby SspiNegotiation/Kerberos. Tożsamość adresu docelowego musi być tożsamością UPN (na przykład acmedomain\\\alice) lub tożsamością SPN (na przykład host/bobs-Machine).|
|CannotFindCert|Nie można znaleźć certyfikatu X. 509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, findtype, findValue.|
|CannotFindCertForTarget|Nie można znaleźć certyfikatu X. 509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, findtype, findValue dla określonego celu.|
|CannotFindCorrelationStateForApplyingSecurity|Nie można znaleźć stanu korelacji dla zastosowania zabezpieczeń do odpowiedzi na obiekt odpowiadający.|
|CannotFindNegotiationState|Nie można znaleźć stanu negocjowania dla określonego kontekstu.|
|CannotFindSecuritySession|Nie można znaleźć sesji zabezpieczeń o określonym IDENTYFIKATORze.|
|CannotImportProtectionLevelForContract|Zasady importowania procesu nie mogą zaimportować powiązania dla określonego kontraktu. Wymagania dotyczące ochrony dla powiązania nie są zgodne z powiązaniem już zaimportowanym dla kontraktu. Należy ponownie skonfigurować powiązanie.|
|CannotImportSupportingTokensForOperationWithoutRequestAction|Importowanie zasad zabezpieczeń nie powiodło się. Zasady zabezpieczeń zawierają wymagania dotyczące tokenu pomocniczego w zakresie operacji. Opis kontraktu nie określa akcji dla komunikatu żądania skojarzonego z tą operacją.|
|CannotIssueRstTokenType|Nie można wystawić tokenu lub określonego typu.|
|CannotObtainIssuedTokenKeySize|Nie można określić rozmiaru klucza wystawionego tokenu.|
|CannotPerformImpersonationOnUsernameToken|Personifikacja przy użyciu tokenu klienta nie jest możliwa. Określone powiązanie dla określonego kontraktu używa tokenu zabezpieczeń username do uwierzytelniania klienta przy użyciu zarejestrowanego dostawcy członkostwa. Użyj innego typu tokenu zabezpieczającego dla klienta.|
|CannotPerformS4UImpersonationOnPlatform|Określone powiązanie dla określonego kontraktu obsługuje personifikację tylko w systemie Windows Server 2003 i nowszych wersjach systemu Windows. Użyj uwierzytelniania SspiNegotiated i powiązania z bezpieczną konwersacją z włączonym anulowaniem.|
|CannotReadKeyIdentifier|Nie można odczytać identyfikatora z określonego elementu z określoną przestrzenią nazw.|
|CannotReadToken|Nie można odczytać tokenu z określonego elementu z określoną przestrzenią nazw dla elementem BinarySecretSecurityToken z określonym elementem ValueType. Jeśli ten element będzie prawidłowy, upewnij się, że zabezpieczenia są skonfigurowane do używania tokenów z określoną nazwą, przestrzenią nazw i typem wartości.|
|CertificateUnsupportedForHttpTransportCredentialOnly|Uwierzytelnianie klienta oparte na certyfikatach nie jest obsługiwane w trybie zabezpieczeń TransportCredentialOnly. Wybierz tryb zabezpieczeń transport.|
|ClaimTypeCannotBeEmpty|Element ClaimType nie może być pustym ciągiem.|
|ClientCertificateNotProvided|Nie dostarczono certyfikatu dla klienta. Certyfikat można ustawić w obiekcie ClientCredentials lub ServiceCredentials.|
|ClientCredentialTypeMustBeSpecifiedForMixedMode|Obiekt ClientCredentialtype. None nie jest prawidłowy dla trybu zabezpieczeń TransportWithMessageCredential. Określ typ poświadczeń lub użyj innego trybu zabezpieczeń.|
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Schemat konfiguracji jest niewystarczający do opisania niestandardowej konfiguracji następującego elementu powiązania zabezpieczeń:|
|DerivedKeyTokenGenerationAndLengthTooHigh|Określona generacja i długość klucza pochodnego spowoduje, że przesunięcia wyprowadzania klucza przekracza maksymalne dozwolone przesunięcie.|
|DnsIdentityCheckFailedForIncomingMessage|Nie można sprawdzić tożsamości komunikatu przychodzącego. Określono oczekiwaną tożsamość systemu nazw domen (DNS) zdalnego punktu końcowego. Zdalny punkt końcowy podał określone zastrzeżenie systemu nazw domen (DNS). Jeśli jest to uprawniony zdalny punkt końcowy, można naprawić ten problem, określając tożsamość systemu nazw domen jako właściwość tożsamości elementu EndpointAddress podczas tworzenia serwera proxy kanału.|
|DnsIdentityCheckFailedForOutgoingMessage|Sprawdzenie tożsamości nie powiodło się dla komunikatu, który został wychodzący. Zdalny punkt końcowy powinien mieć określoną tożsamość systemu nazw domen. Zdalny punkt końcowy podał zastrzeżenie systemu nazw domen (DNS). Jeśli jest to uprawniony zdalny punkt końcowy, można rozwiązać ten problem, jawnie określając tożsamość DNS jako właściwość Identity elementu EndpointAddress podczas tworzenia serwera proxy kanału.|
|DuplicateIdInMessageToBeVerified|Określony identyfikator wystąpił dwukrotnie w komunikacie dostarczonym do weryfikacji.|
|EmptyBase64Attribute|Znaleziono pustą wartość dla wymaganej nazwy i przestrzeni nazw atrybutu Base-64.|
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Eksportowanie zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element element AsymmetricSecurityBindingElement i bezpiecznego powiązania transportowego. Eksport zasad dla takiego powiązania nie jest obsługiwany.|
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Eksportowanie zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element SymmetricSecurityBindingElement i bezpiecznego powiązania transportowego. Eksport zasad dla takiego powiązania nie jest obsługiwany.|
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Eksportowanie zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element TransportSecurityBindingElement, ale nie ma elementu powiązania transportu implementującego ITransportTokenAssertionProvider. Eksport zasad dla takiego powiązania nie jest obsługiwany. Upewnij się, że element powiązania transportowego w powiązaniu implementuje interfejs ITransportTokenAssertionProvider.|
|FoundMultipleCerts|Znaleziono wiele certyfikatów X. 509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, findtype, findValue. Podaj bardziej konkretną wartość wyszukiwania.|
|FoundMultipleCertsForTarget|Znaleziono wiele certyfikatów X. 509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, findtype, findValue dla określonego celu. Podaj bardziej konkretną wartość wyszukiwania.|
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Element SecurityVersion. WSSecurityJan2004 nie obsługuje odszyfrowywania nagłówka. Użyj element SecurityVersion. WsSecurityXXX2005 lub nowszego lub Użyj zabezpieczeń transportu, aby zaszyfrować pełną wiadomość.|
|IdentityCheckFailedForIncomingMessage|Nie można sprawdzić tożsamości komunikatu przychodzącego. Oczekiwana tożsamość jest określona dla docelowego punktu końcowego.|
|IdentityCheckFailedForOutgoingMessage|Nie można sprawdzić tożsamości komunikatu wychodzącego. Oczekiwana tożsamość jest określona dla docelowego punktu końcowego.|
|IncorrectSpnOrUpnSpecified|Uwierzytelnianie interfejsu dostawcy obsługi zabezpieczeń (SSPI) nie powiodło się. Serwer może nie działać na koncie o określonej tożsamości. Jeśli serwer jest uruchomiony na koncie usługi (na przykład w usłudze sieciowej), określ element ServicePrincipalName konta jako tożsamość w elemencie EndpointAddress dla serwera. Jeśli serwer jest uruchomiony na koncie użytkownika, określ wartość UserPrincipalName konta jako tożsamość w elemencie EndpointAddress dla serwera.|
|InvalidAttributeInSignedHeader|Określony nagłówek z podpisem zawiera określony atrybut. Określono oczekiwany atrybut.|
|InvalidCloseResponseAction|Odebrano odpowiedź zamknięcia sesji zabezpieczeń z określoną nieprawidłową akcją.|
|InvalidQName|Nieprawidłowa nazwa QName.|
|InvalidRenewResponseAction|Odebrano odpowiedź odnowienia sesji zabezpieczeń z określoną nieprawidłową akcją.|
|InvalidSspiNegotiation|Negocjowanie interfejsu dostawcy obsługi zabezpieczeń nie powiodło się.|
|IssuerBindingNotPresentInTokenRequirement|Menedżer tokenów zabezpieczających wymaga określenia elementu powiązania zabezpieczeń Bootstrap w wymaganiu tokenu opisującym bezpieczną konwersację. Wymaganie tokenu jest określone w następujący sposób.|
|KeyLengthMustBeMultipleOfEight|Określona długość klucza nie jest wielokrotnością liczby 8 dla kluczy symetrycznych.|
|LsaAuthorityNotContacted|Wewnętrzny błąd protokołu SSL (Zobacz kod stanu Win32, aby uzyskać szczegółowe informacje). Sprawdź certyfikat serwera, aby określić, czy ma on możliwość wymiany kluczy.|
|MaximumPolicyRedirectionsExceeded|Osiągnięto limit cyklicznego pobierania zasad. Sprawdź, czy w łańcuchu usługi federacyjnej występuje pętla.|
|MessagePartSpecificationMustBeImmutable|Specyfikacja części wiadomości musi być stała przed ustawieniem.|
|MissingCustomCertificateValidator|X509CertificateValidationMode. Custom wymaga CustomCertificateValidator. Określ Właściwość CustomCertificateValidator.|
|MissingCustomUserNamePasswordValidator|UserNamePasswordValidationMode. Custom wymaga CustomUserNamePasswordValidator. Określ właściwość CustomUserNamePasswordValidator.|
|MissingMembershipProvider|UserNamePasswordValidationMode. MembershipProvider wymaga MembershipProvider. Określ właściwość MembershipProvider.|
|NoBinaryNegoToSend|Nie wysłano negocjacji binarnej do drugiej strony.|
|NoEncryptionPartsSpecified|Nie określono części komunikatów szyfrowania dla komunikatów z określoną akcją.|
|NoKeyInfoInEncryptedItemToFindDecryptingToken|Nie znaleziono wartości KeyInfo w zaszyfrowanym elemencie w celu znalezienia tokenu odszyfrowywania.|
|NonceLengthTooShort|Określony identyfikator jednorazowy jest za krótki. Minimalna wymagana długość identyfikatora jednorazowego to 4 bajty.|
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Brak dostępnego wychodzącego elementu EndpointAddress do sprawdzenia tożsamości w wiadomości, która ma zostać wysłana.|
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Brak dostępnego wychodzącego elementu EndpointAddress do sprawdzenia tożsamości odebranej odpowiedzi.|
|NoPartsOfMessageMatchedPartsToSign|Nie utworzono podpisu, ponieważ żadna część komunikatu nie pasuje do podanej specyfikacji części wiadomości.|
|NoPrincipalSpecifiedInAuthorizationContext|W kontekście autoryzacji nie określono niestandardowego podmiotu zabezpieczeń.|
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Brak sygnatury w nagłówku zabezpieczeń, aby zapewnić identyfikator jednorazowy wykrywania powtarzania.|
|NoSignaturePartsSpecified|Nie określono części komunikatu sygnatury dla komunikatów z określoną akcją.|
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Brak dostępnego tokenu podpisywania, aby przeprowadzić kontrolę tożsamości przychodzącej.|
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Sygnatura czasowa nie jest dostępna w nagłówku zabezpieczeń, aby można było wykrywać powtarzanie.|
|NoTransportTokenAssertionProvided|Ekspert zasad zabezpieczeń nie powiódł się. Podane potwierdzenie tokenu transportu określonego typu nie utworzyło potwierdzenia tokenu transportu w celu uwzględnienia potwierdzenia zasad zabezpieczeń SP: TransportBinding.|
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Symetryczny protokół zabezpieczeń można skonfigurować za pomocą dostawcy tokenu symetrycznego oraz wystawcy uwierzytelnienia tokenu symetrycznego lub asymetrycznego dostawcę tokenu. Nie można go skonfigurować przy użyciu obu tych metod.|
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Tej operacji nie można wykonać w nagłówkach zabezpieczeń odbiorcy.|
|OperationDoesNotAllowImpersonation|Określona operacja usługi, która należy do kontraktu o określonej nazwie i przestrzeni nazw, nie zezwala na personifikację.|
|PolicyRequiresConfidentialityWithoutIntegrity|Zasady zabezpieczeń komunikatów dla określonej akcji wymagają poufności bez integralności. Poufność bez integralności nie jest obsługiwana.|
|PrimarySignatureIsRequiredToBeEncrypted|Podpis podstawowy musi być zaszyfrowany.|
|PropertySettingErrorOnProtocolFactory|Wymagana właściwość w określonej fabryce protokołu zabezpieczeń nie została ustawiona lub ma nieprawidłową wartość.|
|ProtocolFactoryCouldNotCreateProtocol|Fabryka protokołów nie może utworzyć protokołu.|
|PublicKeyNotRSA|Klucz publiczny nie jest kluczem RSA.|
|RequiredMessagePartNotEncrypted|Określona część wymaganego komunikatu nie została zaszyfrowana.|
|RequiredMessagePartNotEncryptedNs|Określona część wymaganego komunikatu nie została zaszyfrowana.|
|RequiredMessagePartNotSigned|Określona część wymaganego komunikatu nie została podpisana.|
|RequiredMessagePartNotSignedNs|Określona część wymaganego komunikatu nie została podpisana.|
|RequiredSecurityHeaderElementNotSigned|Określony element nagłówka zabezpieczeń o określonym IDENTYFIKATORze musi być podpisany.|
|RequiredSecurityTokenNotEncrypted|Określony token zabezpieczający z określonym trybem załącznika musi być zaszyfrowany.|
|RequiredSecurityTokenNotSigned|Określony token zabezpieczający z określonym trybem załącznika musi być podpisany.|
|RequiredSignatureMissing|Podpis musi znajdować się w nagłówku zabezpieczeń.|
|RequireNonCookieMode|Określone powiązanie z określoną przestrzenią nazw jest skonfigurowane do wystawiania tokenów kontekstu zabezpieczeń plików cookie. Usługi integracji COM+ nie obsługują tokenów kontekstu zabezpieczeń plików cookie.|
|RevertingPrivilegeFailed|Operacja przywracania nie powiodła się z powodu określonego wyjątku.|
|RSTRAuthenticatorIncorrect|Element RequestSecurityTokenResponse CombinedHash jest nieprawidłowy.|
|SecureConversationCancelNotAllowedFaultReason|Powiązanie nie zezwala na anulowanie bezpiecznej konwersacji.|
|SecureConversationDriverVersionDoesNotSupportSession|Skonfigurowana wersja SecureConversation nie obsługuje sesji. Użyj WSSecureConversationFeb2005 lub nowszego.|
|SecureConversationRequiredByReliableSession|Nie można ustanowić niezawodnej sesji bez bezpiecznej konwersacji. Włącz bezpieczną konwersację.|
|SecurityAuditFailToLoadDll|Nie można załadować określonej biblioteki dołączanej dynamicznie (dll).|
|SecurityAuditNotSupportedOnChannelFactory|SecurityAuditBehavior nie jest obsługiwana w fabryce kanałów.|
|SecurityAuditPlatformNotSupported|Bieżąca platforma nie obsługuje zapisywania komunikatów inspekcji w dzienniku zabezpieczeń. Należy napisać komunikaty inspekcji do dziennika aplikacji.|
|SecurityBindingElementCannotBeExpressedInConfig|Zaimportowano zasady zabezpieczeń dla punktu końcowego. Zasady zabezpieczeń zawierają wymagania, których nie można reprezentować w konfiguracji Windows Communication Foundation. Wyszukaj komentarz dotyczący parametrów elementu SecurityBindingElement wymaganych w wygenerowanym pliku konfiguracyjnym. Utwórz poprawny element powiązania z kodem. Konfiguracja powiązania, która znajduje się w pliku konfiguracji, nie jest bezpieczna.|
|SecurityBindingSupportsOneWayOnly|Zabezpieczeniabinding dla określonego powiązania dla określonego kontraktu obsługują tylko operację OneWay.|
|SecurityContextDoesNotAllowImpersonation|Nie można rozpocząć personifikacji, ponieważ element SecurityContext roli UltimateReceiver z komunikatu żądania z określoną akcją nie jest zamapowany na tożsamość systemu Windows.|
|SecurityListenerClosing|Odbiornik nie akceptuje nowych bezpiecznych konwersacji, ponieważ jest zamykany.|
|SecurityListenerClosingFaultReason|Serwer nie akceptuje obecnie nowych bezpiecznych konwersacji, ponieważ trwa jego zamykanie. Spróbuj ponownie później.|
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Przed wykonaniem tej operacji należy ustawić fabrykę protokołów zabezpieczeń.|
|SecuritySessionAbortedFaultReason|Sesja zabezpieczeń została przerwana. Może to być spowodowane tym, że żadne komunikaty nie zostały odebrane w sesji przez zbyt długo.|
|SecuritySessionKeyIsStale|Należy odnowić klucz sesji, aby można było zabezpieczyć komunikaty aplikacji.|
|SecuritySessionLimitReached|Nie można utworzyć sesji zabezpieczeń. Spróbuj ponownie później.|
|SecuritySessionNotPending|Brak oczekujących sesji zabezpieczeń o określonym IDENTYFIKATORze.|
|SecurityTokenParametersHasIncompatibleInclusionMode|Określone powiązanie jest skonfigurowane przy użyciu parametru tokenu zabezpieczającego, który ma określony niezgodny tryb dołączania tokenu zabezpieczeń. Określ alternatywny tryb dołączania tokenu zabezpieczającego.|
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Określone powiązanie dla określonego kontraktu zostało skonfigurowane przy użyciu niezgodnej wersji zabezpieczeń, która nie obsługuje niedołączonych odwołań do EncryptedKeys. Użyj określonej wartości lub wyższej jako wersji zabezpieczeń dla powiązania.|
|SecurityVersionDoesNotSupportSignatureConfirmation|Określony element SecurityVersion nie obsługuje potwierdzenia podpisu. Użyj nowszej element SecurityVersion.|
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Określone powiązanie dla określonego kontraktu ma skonfigurowaną wersję zabezpieczeń, która nie obsługuje odwołań zewnętrznych do tokenów X. 509 przy użyciu wartości odcisku palca certyfikatu. Użyj określonej wartości lub wyższej jako wersji zabezpieczeń dla powiązania.|
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Należy określić parametry tokenu zabezpieczającego z Tokenami pomocniczymi dla każdego komunikatu.|
|ServerCertificateNotProvided|Odbiorca nie dostarczył swojego certyfikatu. Ten certyfikat jest wymagany przez protokół TLS. Obie strony muszą mieć dostęp do swoich certyfikatów.|
|SignatureConfirmationNotSupported|Skonfigurowany element SecurityVersion nie obsługuje potwierdzenia podpisu. Użyj WSSecurityXXX2005 lub nowszego.|
|SignatureConfirmationRequiresRequestReply|Fabryka protokołów musi obsługiwać zabezpieczenia żądania/odpowiedzi, aby można było oferować potwierdzenie podpisu.|
|SignatureNotExpected|Sygnatura nie jest oczekiwana dla tego komunikatu.|
|SigningTokenHasNoKeys|Określony token podpisujący nie ma kluczy. Token zabezpieczający jest używany w kontekście, który wymaga wykonania operacji kryptograficznych, ale token nie zawiera kluczy kryptograficznych. Typ tokenu nie obsługuje operacji kryptograficznych lub określone wystąpienie tokenu nie zawiera kluczy kryptograficznych. Sprawdź konfigurację, aby upewnić się, że kryptograficznie wyłączone typy tokenów (na przykład elementu UserNameSecurityToken) nie są określone w kontekście, który wymaga operacji kryptograficznych (na przykład tokenu wspomagającego zatwierdzenie).|
|SpnegoImpersonationLevelCannotBeSetToNone|Interfejs dostawcy obsługi zabezpieczeń nie obsługuje poziomu personifikacji "Brak". Określ identyfikator, personifikację lub poziom delegowania.|
|SslClientCertMustHavePrivateKey|Określony certyfikat musi mieć klucz prywatny. Proces musi mieć prawa dostępu do klucza prywatnego.|
|SslServerCertMustDoKeyExchange|Określony certyfikat musi mieć klucz prywatny obsługujący wymianę kluczy. Proces musi mieć prawa dostępu do klucza prywatnego.|
|StandardsManagerCannotWriteObject|Serializator tokenu nie może serializować określonego obiektu.  Jeśli jest to typ niestandardowy, należy podać serializator niestandardowy.|
|TimeStampHasCreationAheadOfExpiry|Sygnatura czasowa zabezpieczeń jest nieprawidłowa, ponieważ jej czas utworzenia jest większy lub równy czasowi wygaśnięcia.|
|TimeStampHasCreationTimeInFuture|Sygnatura czasowa zabezpieczeń jest nieprawidłowa, ponieważ jej godzina utworzenia jest w przyszłości. Bieżący czas jest określony, a określono dozwolone przechylenie zegara.|
|TimeStampHasExpiryTimeInPast|Sygnatura czasowa zabezpieczeń jest nieodświeżona, ponieważ jej godzina wygaśnięcia minęła. Bieżący czas jest określony, a określono dozwolone przechylenie zegara.|
|TimeStampWasCreatedTooLongAgo|Sygnatura czasowa zabezpieczeń jest nieodświeżona, ponieważ jej czas utworzenia jest zbyt zaległy w przeszłości. Bieżący czas, maksymalny okres istnienia sygnatury czasowej i dozwolone przechylenie zegara są określone.|
|TokenProviderCannotGetTokensForTarget|Dostawca tokenu nie może uzyskać tokenów dla określonego celu.|
|TooManyIssuedSecurityTokenParameters|Element nogi łańcucha zabezpieczeń federacyjnych zawiera wiele IssuedSecurityTokenParameters. System InfoCard obsługuje tylko jeden IssuedSecurityTokenParameters dla każdego etapu.|
|TransportDoesNotProtectMessage|Określone powiązanie dla określonego kontraktu jest skonfigurowane z trybem uwierzytelniania wymagającym integralności i poufności poziomu transportu. Jednak transport nie może zapewnić integralności i poufności.|
|TrustApr2004DoesNotSupportCertainIssuedTokens|WSTrustApr2004 nie obsługuje wystawiania certyfikatów X. 509 lub EncryptedKeys. Użyj WsTrustFeb2005 lub nowszego.|
|TrustDriverVersionDoesNotSupportSession|Skonfigurowana wersja zaufania nie obsługuje sesji. Użyj WSTrustFeb2005 lub nowszego.|
|UnableToCreateICryptoFromTokenForSignatureVerification|Nie można utworzyć interfejsu ICrypto z określonego tokenu na potrzeby weryfikacji podpisu.|
|UnableToCreateSymmetricAlgorithmFromToken|Nie można utworzyć określonego algorytmu symetrycznego na podstawie tokenu.|
|UnableToDeriveKeyFromKeyInfoClause|Określona klauzula KeyInfo została rozpoznana jako określony token, który nie zawiera klucza symetrycznego, którego można użyć na potrzeby wyprowadzania.|
|UnableToFindTokenAuthenticator|Nie można znaleźć wystawcy uwierzytelnienia tokenu dla określonego typu tokenu. Tokeny tego typu nie mogą być akceptowane zgodnie z bieżącymi ustawieniami zabezpieczeń.|
|UnableToLoadCertificateIdentity|Nie można załadować tożsamości certyfikatu X. 509 określonej w konfiguracji.|
|UnexpectedEmptyElementExpectingClaim|Określony element z określonego obszaru nazw jest pusty i nie określa prawidłowego żądania tożsamości.|
|UnknownEncodingInBinarySecurityToken|Podczas odczytu binarnego tokenu zabezpieczającego wystąpił nierozpoznane kodowanie.|
|UnsecuredMessageFaultReceived|Odebrano niezabezpieczoną lub nieprawidłowo zabezpieczony błąd od drugiej strony. Zapoznaj się z wewnętrznym licznikiem FaultException, aby poznać kod błędu i szczegóły.|
|UnsupportedPasswordType|Określony token nazwy użytkownika ma nieobsługiwany typ hasła.|
|UnsupportedSecureConversationBootstrapProtectionRequirements|Nie można zaimportować zasad zabezpieczeń. Wymagania dotyczące ochrony dla powiązania ładowania początkowego bezpiecznej konwersacji nie są obsługiwane. Wymagania dotyczące ochrony ładowania początkowego bezpiecznej konwersacji muszą wymagać podpisania i zaszyfrowania zarówno żądania, jak i odpowiedzi.|
|UnsupportedSecurityPolicyAssertion|Wykryto nieobsługiwane potwierdzenie zasad zabezpieczeń podczas określonego importowania zasad zabezpieczeń.|
