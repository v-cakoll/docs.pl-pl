---
title: Wyjątki zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
ms.openlocfilehash: c1eeca9111837b9833de54ecafbc981d1c2b6343
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780864"
---
# <a name="security-exceptions"></a>Wyjątki zabezpieczeń
Ten temat zawiera listę wszystkich wyjątków zabezpieczeń.  
  
## <a name="exception-list"></a>Lista wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|Usługa umożliwia anonimowego logowania.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Komunikat żądania muszą być chronione. Jest to wymagane przez operację określonego zamówienia. Ochrony musi być podana według określonego powiązania.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Komunikat odpowiedzi muszą być chronione. Jest to wymagane przez operację określonego zamówienia. Ochrony musi być podana według określonego powiązania.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|W nagłówku zabezpieczeń dozwolony jest tylko jeden podpis podstawowy.|  
|BadContextTokenFaultReason|Token kontekstu zabezpieczeń wygasło lub jest nieprawidłowy. Wiadomość nie została przetworzona.|  
|BadEncryptionState|Element EncryptedData lub EncryptedKey jest w nieprawidłowym stanie dla tej operacji.|  
|BasicHttpMessageSecurityRequiresCertificate|Powiązanie BasicHttp wymaga, aby typ BasicHttpBinding.Security.Message.ClientCredentialType do poświadczeń BasicHttpMessageCredentialType.Certificate dla bezpiecznych komunikatów. Wybierz opcję zabezpieczeń Transport lub TransportWithMessageCredential dla poświadczeń UserName.|  
|BasicTokenCannotBeWrittenWithoutEncryption|Nie można zapisać token podstawowy bez szyfrowania.|  
|BindingDoesNotSupportProtectionForRst|Określone powiązanie dla określonego kontraktu jest skonfigurowany przy użyciu mechanizmu SecureConversation, ale tryb uwierzytelniania nie jest w stanie/odpowiedzi na podstawie żądań integralności i poufności informacji wymaganych do negocjacji.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|Operacja kontrakt określony wymaga tożsamości Windows automatyczne personifikacji. Tożsamość Windows, który reprezentuje obiekt wywołujący nie zostanie podany przez określone powiązanie dla określonej umowy.|  
|CachedNegotiationStateQuotaReached|Usługa nie może w pamięci podręcznej stanu negocjacji zgodnie z określoną pojemność został osiągnięty. Ponów żądanie.|  
|CacheQuotaReached|Nie można dodać elementu. Maksymalny rozmiar pamięci podręcznej jest określony.|  
|CannotDetermineSPNBasedOnAddress|Klient nie może określić, że nazwa główna usługi na podstawie tożsamości z adresu określonego obiektu docelowego na potrzeby SspiNegotiation/Kerberos. Tożsamość adresu docelowego musi być tożsamością UPN (jak domena_abc\\\alice) lub tożsamością SPN (jak host/komputer1).|  
|CannotFindCert|Nie można odnaleźć certyfikatu X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Nie można odnaleźć certyfikatu X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue dla określonego celu.|  
|CannotFindCorrelationStateForApplyingSecurity|Nie można odnaleźć stanu korelacji stosowania zabezpieczeń do odpowiedzi na odpowiadający.|  
|CannotFindNegotiationState|Nie można odnaleźć stanu negocjacji dla określonego kontekstu.|  
|CannotFindSecuritySession|Nie można odnaleźć sesji zabezpieczeń o określonym identyfikatorze.|  
|CannotImportProtectionLevelForContract|Zasady importu procesu nie można importować powiązania dla kontraktu określony. Wymagania dotyczące ochrony dla powiązania są niezgodne z powiązaniem został już zaimportowany w ramach umowy. Należy ponownie skonfigurować powiązanie.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Nie można zaimportować zasad zabezpieczeń. Zasady zabezpieczeń zawierają wymagania tokenu pomocniczego w zakresie operacji. Opis kontraktu nie określa akcji dla komunikatu żądania skojarzonego z tą operacją.|  
|CannotIssueRstTokenType|Nie można wystawić tokenu lub określonego typu.|  
|CannotObtainIssuedTokenKeySize|Nie można określić rozmiar klucza wystawiony token.|  
|CannotPerformImpersonationOnUsernameToken|Personifikacji przy użyciu tokenu klienta nie jest możliwe. Określonego powiązania dla kontraktu określony za pomocą tokenu zabezpieczeń nazwy użytkownika do uwierzytelnienia klienta dostawcy członkostwa, zarejestrowany. Użyj innego typu tokenu zabezpieczającego dla klienta.|  
|CannotPerformS4UImpersonationOnPlatform|Określonego powiązania dla kontraktu określonego obsługuje personifikacji tylko na [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] i nowszych wersji systemu Windows. Za pomocą uwierzytelniania SspiNegotiated i powiązanie Secure konwersacji w przypadku anulowania włączone.|  
|CannotReadKeyIdentifier|Nie można odczytać KeyIdentifier z określonego elementu z określonego obszaru nazw.|  
|CannotReadToken|Nie można odczytać tokenu z określonego elementu z określonego obszaru nazw dla elementu BinarySecretSecurityToken, z określonego obiektu ValueType. Jeśli ten element powinien być prawidłowy, upewnij się, że skonfigurować zabezpieczenia, aby obsługiwały tokeny o nazwie, określić przestrzeń nazw i typie wartości.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|Uwierzytelnianie klienta oparte na certyfikatach jest nieobsługiwane w trybie zabezpieczeń TransportCredentialOnly. Wybierz tryb zabezpieczeń Transport.|  
|ClaimTypeCannotBeEmpty|Element claimType nie może być ciągiem pustym.|  
|ClientCertificateNotProvided|Nie podano certyfikatu klienta. Certyfikat można ustawić na użyciu obiektu ClientCredentials lub ServiceCredentials.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|Wartość ClientCredentialType.None jest nieprawidłowa dla trybu zabezpieczeń TransportWithMessageCredential. Określanie typu poświadczeń lub użyj innego trybu zabezpieczeń.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Schemat konfiguracji jest niewystarczający do opisania niestandardowej konfiguracji następującego elementu powiązania zabezpieczeń:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|Klucza pochodnego określone generowania i długość wyniku w przesunięcie wyprowadzenia klucza, która jest większa niż maksymalna przesunięcie dozwolone.|  
|DnsIdentityCheckFailedForIncomingMessage|Nie można sprawdzić tożsamości komunikatu przychodzącego. Określono tożsamość system (DNS) nazwa domeny oczekiwanego zdalnego punktu końcowego. Zdalny punkt końcowy podana oświadczeń określona domena systemu nazw (domen DNS). Jeśli jest to uprawniony zdalny punkt końcowy, można naprawić ten problem, określając tożsamość systemu nazw domen jako właściwość identity elementu EndpointAddress podczas tworzenia serwera proxy kanału.|  
|DnsIdentityCheckFailedForOutgoingMessage|Nie można sprawdzić tożsamości komunikatu, który został przejściem się. Zdalny punkt końcowy powinny mieć tożsamość systemowej nazwy określonej domeny. Zdalny punkt końcowy udostępnił o tym, system nazw domen (DNS) oświadczenia. Jeśli jest to uprawniony zdalny punkt końcowy, można rozwiązać problem, jawnie ustawiając tożsamość DNS jako właściwość Identity elementu EndpointAddress podczas tworzenia serwera proxy kanału.|  
|DuplicateIdInMessageToBeVerified|Określony identyfikator wystąpił dwa razy w wiadomości, która jest dostarczana w celu weryfikacji.|  
|EmptyBase64Attribute|Znaleziono pustą wartość dla nazwy wymaganego atrybutu base-64 i przestrzeni nazw.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Eksport zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element AsymmetricSecurityBindingElement i element powiązania transportu bezpieczne. Eksportowanie zasad dla takiego powiązania nie jest obsługiwana.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Eksport zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element SymmetricSecurityBindingElement i element powiązania transportu bezpieczne. Eksportowanie zasad dla takiego powiązania nie jest obsługiwana.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Eksport zasad zabezpieczeń nie powiodło się. Wiązanie zawiera TransportSecurityBindingElement, ale żaden element powiązania transportu implementującego ITransportTokenAssertionProvider. Eksportowanie zasad dla takiego powiązania nie jest obsługiwana. Upewnij się, że powiązanie element powiązania transportu implementuje interfejs ITransportTokenAssertionProvider.|  
|FoundMultipleCerts|Znaleziono wiele certyfikatów X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue. Podaj dokładniejszą wartość wyszukiwania.|  
|FoundMultipleCertsForTarget|Znaleziono wiele certyfikatów X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue dla określonego celu. Podaj dokładniejszą wartość wyszukiwania.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Element SecurityVersion.WSSecurityJan2004 nie obsługuje nagłówka odszyfrowywania. Użyj SecurityVersion.WsSecurityXXX2005 i nowsze wersje lub zaszyfrować cały komunikat za pomocą zabezpieczeń transportu.|  
|IdentityCheckFailedForIncomingMessage|Nie można sprawdzić tożsamości komunikatu przychodzącego. Oczekiwaną tożsamość jest określona dla docelowego punktu końcowego.|  
|IdentityCheckFailedForOutgoingMessage|Nie można sprawdzić tożsamości komunikatu wychodzącego. Oczekiwaną tożsamość jest określona dla docelowego punktu końcowego.|  
|IncorrectSpnOrUpnSpecified|Uwierzytelnianie interfejsu dostawcy obsługi (SSPI) zabezpieczeń nie powiodło się. Serwer nie może być uruchomiony w ramach konta o określonej tożsamości. Jeśli serwer jest uruchomiony na koncie usługi (na przykład usługi sieciowej), należy określić element ServicePrincipalName konta jako tożsamość w EndpointAddress dla serwera. Jeśli serwer jest uruchomiony na koncie użytkownika, należy określić UserPrincipalName konta jako tożsamość w EndpointAddress dla serwera.|  
|InvalidAttributeInSignedHeader|Określony nagłówek podpisem zawiera określonego atrybutu. Oczekiwany atrybut jest określony.|  
|InvalidCloseResponseAction|Odebrano odpowiedź Zamknij sesję zabezpieczeń z określoną nieprawidłową akcję.|  
|InvalidQName|Nazwa QName jest nieprawidłowe.|  
|InvalidRenewResponseAction|Sesja zabezpieczeń odnowić odpowiedź została odebrana z określoną nieprawidłową akcję.|  
|InvalidSspiNegotiation|Nie można wynegocjować interfejsu dostawcy obsługi zabezpieczeń.|  
|IssuerBindingNotPresentInTokenRequirement|Menedżer tokenów zabezpieczeń wymaga elementu powiązania zabezpieczeń dla uruchamiania, należy określić wymaganie tokenu, który opisuje bezpiecznej konwersacji. Wymaganie tokenu jest określona w następujący sposób.|  
|KeyLengthMustBeMultipleOfEight|Określona długość klucza nie jest wielokrotnością liczby 8 dla kluczy symetrycznych.|  
|LsaAuthorityNotContacted|Błąd wewnętrzny protokołu SSL (zobacz kod stanu systemu Win32, aby uzyskać szczegółowe informacje). Sprawdź certyfikat serwera, aby ustalić, czy jest w stanie wymiany kluczy.|  
|MaximumPolicyRedirectionsExceeded|Osiągnięto limit cyklicznego pobierania zasad. Sprawdź, czy istnieje pętla w łańcuchu usług federacyjnych.|  
|MessagePartSpecificationMustBeImmutable|Specyfikacja części wiadomości musi nastąpić stałej zanim zostanie ustawiona.|  
|MissingCustomCertificateValidator|Element X509CertificateValidationMode.Custom wymaga CustomCertificateValidator. Określ właściwość CustomCertificateValidator.|  
|MissingCustomUserNamePasswordValidator|Element UserNamePasswordValidationMode.Custom wymaga CustomUserNamePasswordValidator. Określ właściwość CustomUserNamePasswordValidator.|  
|MissingMembershipProvider|Element UserNamePasswordValidationMode.MembershipProvider wymaga MembershipProvider. Określ właściwość MembershipProvider.|  
|NoBinaryNegoToSend|Negocjacji binarnej została wysłana do drugiej strony.|  
|NoEncryptionPartsSpecified|Nie części wiadomości szyfrowania zostały określone dla komunikatów z określonej akcji.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|Nie znaleziono wartości KeyInfo w elemencie zaszyfrowane, można znaleźć odszyfrowywania tokenu.|  
|NonceLengthTooShort|Określony identyfikator jednorazowy jest zbyt krótki. Minimalna wymagana długość identyfikatora jednorazowego wynosi 4 bajty.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Nie wychodzących EndpointAddress jest dostępne sprawdzić tożsamość wiadomości do wysłania.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Nie wychodzących EndpointAddress jest dostępny sprawdzić tożsamość Odebrano odpowiedź.|  
|NoPartsOfMessageMatchedPartsToSign|Podpis nie został utworzony, ponieważ żadna część komunikatu dopasowane Specyfikacja części dostarczony komunikat.|  
|NoPrincipalSpecifiedInAuthorizationContext|Nie niestandardowy podmiot zabezpieczeń jest określona w kontekście autoryzacji.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Podpis nie jest dostępna w nagłówku zabezpieczeń do zapewnienia identyfikator jednorazowy wykrywania powtarzania.|  
|NoSignaturePartsSpecified|Nie określono żadnych części podpisu wiadomości dla wiadomości z określonej akcji.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Brak podpisywania tokenu jest dostępny dla przychodzących sprawdzanie tożsamości.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Brak sygnatury czasowej jest dostępna w nagłówku zabezpieczeń do wykrywania powtarzania.|  
|NoTransportTokenAssertionProvided|Nie można wyeksportować zasad zabezpieczeń. Dostarczona asercja tokenu transportu określonego typu nie utworzyła asercji tokenu transportu w celu uwzględnienia asercję zasad zabezpieczeń SP: TransportBinding.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Protokół zabezpieczeń symetrycznego może być skonfigurowany przy użyciu dostawcy tokenu symetrycznego i wystawcy uwierzytelnienia tokenu symetrycznego lub asymetrycznego dostawcy tokenu. Nie można skonfigurować za pomocą obu.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Nie można wykonać tej operacji na nagłówki zabezpieczeń odbiorcy.|  
|OperationDoesNotAllowImpersonation|Operacja określonej usługi, która należy do Umowy o określonej nazwie i przestrzeni nazw nie umożliwia personifikacji.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Zasada zabezpieczeń wiadomości dla określonej akcji wymaga poufności bez integralności. Poufność bez integralności nie jest obsługiwane.|  
|PrimarySignatureIsRequiredToBeEncrypted|Podpis podstawowy musi być szyfrowana.|  
|PropertySettingErrorOnProtocolFactory|Wymagana właściwość fabryki protokołów zabezpieczeń określonego nie jest ustawiona lub ma nieprawidłową wartość.|  
|ProtocolFactoryCouldNotCreateProtocol|Fabryka protokołów nie może utworzyć protokołu.|  
|PublicKeyNotRSA|Klucz publiczny nie jest kluczem RSA.|  
|RequiredMessagePartNotEncrypted|Część określony komunikat wymagana nie została zaszyfrowana.|  
|RequiredMessagePartNotEncryptedNs|Część określony komunikat wymagana nie została zaszyfrowana.|  
|RequiredMessagePartNotSigned|Część określony komunikat wymagana nie został podpisany.|  
|RequiredMessagePartNotSignedNs|Część określony komunikat wymagana nie został podpisany.|  
|RequiredSecurityHeaderElementNotSigned|Musi być podpisany element nagłówka zabezpieczeń określone o określonym identyfikatorze.|  
|RequiredSecurityTokenNotEncrypted|Określony "token zabezpieczeń z trybem określonego załącznika musi być szyfrowana.|  
|RequiredSecurityTokenNotSigned|Musi być podpisany token zabezpieczeń określone w trybie określonego załącznika.|  
|RequiredSignatureMissing|Podpis musi być w nagłówku zabezpieczenia.|  
|RequireNonCookieMode|Określone powiązanie z określonego obszaru nazw jest skonfigurowany do wystawiania tokenów kontekstów plik cookie zabezpieczeń. Usługi integracji COM + nie obsługuje tokeny kontekstu zabezpieczeń pliku cookie.|  
|RevertingPrivilegeFailed|Operacja przywracania nie powiodło się z określonym wyjątkiem.|  
|RSTRAuthenticatorIncorrect|RequestSecurityTokenResponse CombinedHash jest nieprawidłowy.|  
|SecureConversationCancelNotAllowedFaultReason|Unieważnieniu bezpiecznej konwersacji nie jest dozwolona przez powiązanie.|  
|SecureConversationDriverVersionDoesNotSupportSession|Skonfigurowana wersja mechanizmu SecureConversation nie obsługuje sesji. Użyj wersji WSSecureConversationFeb2005 lub nowszej.|  
|SecureConversationRequiredByReliableSession|Nie można utworzyć niezawodnej sesji bez bezpiecznej konwersacji. Włącz obsługę bezpiecznej konwersacji.|  
|SecurityAuditFailToLoadDll|Nie można załadować określonej biblioteki dołączanej dynamicznie (dll).|  
|SecurityAuditNotSupportedOnChannelFactory|Element SecurityAuditBehavior nie jest obsługiwana na fabryki kanałów.|  
|SecurityAuditPlatformNotSupported|Bieżąca platforma nie jest obsługiwana zapisywania komunikatów inspekcji do dziennika zabezpieczeń. Komunikaty inspekcji należy zapisywać do dziennika aplikacji.|  
|SecurityBindingElementCannotBeExpressedInConfig|Nie zaimportowano zasadę zabezpieczeń dla punktu końcowego. Zasada zabezpieczeń zawiera wymagania, których nie można przedstawić w konfiguracji programu Windows Communication Foundation. Poszukaj komentarza dotyczącego parametrów SecurityBindingElement wymaganych w wygenerowanym pliku konfiguracji. Utwórz poprawny element powiązania z kodem. Konfiguracja powiązania w pliku konfiguracji nie jest bezpieczny.|  
|SecurityBindingSupportsOneWayOnly|SecurityBinding dla określonego powiązania dla kontraktu określonego obsługuje tylko operacji o jedną stronę.|  
|SecurityContextDoesNotAllowImpersonation|Nie można uruchomić personifikacji, ponieważ element SecurityContext dla roli UltimateReceiver poza komunikatem żądania z czynnością nie została zamapowana na tożsamość Windows.|  
|SecurityListenerClosing|Odbiornik nie akceptuje nowej bezpiecznej konwersacji, ponieważ jest on zamykany.|  
|SecurityListenerClosingFaultReason|Serwer nie przyjmuje aktualnie rozpoczynać nowe rozmowy bezpieczne, ponieważ jest on zamykany. Spróbuj ponownie później.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Fabryka protokołów zabezpieczeń należy ustawić przed wykonaniem tej operacji.|  
|SecuritySessionAbortedFaultReason|Sesja zabezpieczeń zostało zakończone. Może to być, ponieważ nie otrzymano żadnych komunikatów w sesji jest zbyt długa.|  
|SecuritySessionKeyIsStale|Klucz sesji musi być odnawiany przed jej zabezpieczenia komunikatów aplikacji.|  
|SecuritySessionLimitReached|Nie można utworzyć sesji zabezpieczeń. Spróbuj ponownie później.|  
|SecuritySessionNotPending|Brak sesji zabezpieczeń o określonym identyfikatorze jest w stanie oczekiwania.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|Określone powiązanie jest skonfigurowany z parametru tokenu zabezpieczeń, który ma tryb dołączania tokenu zabezpieczeń niezgodny określone. Określ tryb dołączania tokenu zabezpieczeń alternatywne.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Określone powiązanie dla określonej umowy została skonfigurowana wersją niezgodne zabezpieczeń, która nie obsługuje niedołączone odwołania do kluczy zaszyfrowanych. Użyj określonej wartości lub nowszy w wersji zabezpieczeń dla wiązania.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|Określona wersja SecurityVersion nie obsługuje potwierdzenia podpisu. Użyj nowszego elementu SecurityVersion.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Określone powiązanie dla określonego kontraktu jest skonfigurowany przy użyciu wersji zabezpieczeń, który nie obsługuje odwołań zewnętrznych do tokenów X.509 przy użyciu wartości odcisku palca certyfikatu. Użyj określonej wartości lub nowszy w wersji zabezpieczeń dla wiązania.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Parametry tokenu zabezpieczeń musi być określony z Obsługa tokenów dla każdego komunikatu.|  
|ServerCertificateNotProvided|Odbiorca nie podał swojego certyfikatu. Ten certyfikat jest wymagany przez protokół TLS. Obie strony musi mieć dostęp do swoich certyfikatów.|  
|SignatureConfirmationNotSupported|Skonfigurowana wersja SecurityVersion nie obsługuje potwierdzenia podpisu. Użyj WSSecurityXXX2005 lub nowszej.|  
|SignatureConfirmationRequiresRequestReply|Fabryka protokołów musi obsługiwać zabezpieczeń żądanie/nietypizowana odpowiedź, aby oferować potwierdzenie podpisu.|  
|SignatureNotExpected|Podpis nie jest oczekiwane dla tego komunikatu.|  
|SigningTokenHasNoKeys|Określony token podpisujący nie ma kluczy. Token zabezpieczający jest używany w kontekście, który wymaga wykonywania operacji kryptograficznych, ale token nie zawiera kluczy kryptograficznych. Typ tokenu nie obsługuje operacji kryptograficznych, albo konkretne wystąpienie tokenu nie zawiera kluczy kryptograficznych. Sprawdź konfigurację tak, aby upewnić się, że typy tokenów (na przykład UserNameSecurityToken) nie są określone w kontekście wymagającym operacji kryptograficznych (na przykład tokenu pomocniczego).|  
|SpnegoImpersonationLevelCannotBeSetToNone|Interfejs dostawcy obsługi zabezpieczeń nie obsługuje personifikacji poziomu "None". Określ poziom identyfikacji, personifikacja lub delegowanie.|  
|SslClientCertMustHavePrivateKey|Określony certyfikat musi mieć klucz prywatny. Proces musi mieć prawa dostępu do klucza prywatnego.|  
|SslServerCertMustDoKeyExchange|Określony certyfikat musi mieć klucz prywatny, który jest zdolny do wymiany klucza. Proces musi mieć prawa dostępu do klucza prywatnego.|  
|StandardsManagerCannotWriteObject|Serializator tokenów nie można rozszeregować określonego obiektu.  Jeśli jest to typ niestandardowy, należy użyć serializatora niestandardowego.|  
|TimeStampHasCreationAheadOfExpiry|Sygnatura czasowa zabezpieczeń jest nieprawidłowy, ponieważ jej godzina utworzenia jest większa lub równa godzinie wygaśnięcia.|  
|TimeStampHasCreationTimeInFuture|Sygnatura czasowa zabezpieczeń jest nieprawidłowy, ponieważ jej godzina utworzenia przypada w przyszłości. Bieżący czas jest określony, a dopuszczalna niedokładność zegara jest określona.|  
|TimeStampHasExpiryTimeInPast|Sygnatura czasowa zabezpieczeń jest nieodświeżona, ponieważ jego czas wygaśnięcia jest w przeszłości. Bieżący czas jest określony, a dopuszczalna niedokładność zegara jest określona.|  
|TimeStampWasCreatedTooLongAgo|Sygnatura czasowa zabezpieczeń jest nieodświeżona, ponieważ jej godzina utworzenia jest zbyt daleko w przeszłości. Bieżący czas, okres istnienia maksymalnej sygnaturze, a dopuszczalna niedokładność zegara zostały podane.|  
|TokenProviderCannotGetTokensForTarget|Dostawca tokenu nie można uzyskać tokenów dla określonego docelowego.|  
|TooManyIssuedSecurityTokenParameters|Łańcucha zabezpieczeń zawiera wiele elementów IssuedSecurityTokenParameters. InfoCard system obsługuje tylko jeden element IssuedSecurityTokenParameters dla każdego etapu.|  
|TransportDoesNotProtectMessage|Określone powiązanie dla określonego kontraktu jest skonfigurowany z trybu uwierzytelniania, która wymaga transportu poziomie integralności i poufności. Jednak transportu nie może dostarczyć, integralności i poufności.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|Wersja WSTrustApr2004 nie obsługuje wystawiania certyfikatów X.509 lub kluczy zaszyfrowanych. Skorzystaj z wersji WsTrustFeb2005 lub nowszej.|  
|TrustDriverVersionDoesNotSupportSession|Skonfigurowana wersja Trust nie obsługuje sesji. Skorzystaj z wersji WSTrustFeb2005 lub nowszej.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Nie można utworzyć interfejsu ICrypto na określony token weryfikacji podpisu.|  
|UnableToCreateSymmetricAlgorithmFromToken|Nie można utworzyć określonego algorytmu symetrycznego z tokenu.|  
|UnableToDeriveKeyFromKeyInfoClause|Określonej klauzuli KeyInfo rozwiązane z określonym tokenem, który nie zawiera klucza symetrycznego, które umożliwiają tworzenie wartości pochodnych.|  
|UnableToFindTokenAuthenticator|Nie można znaleźć wystawcy uwierzytelnienia tokenu dla określonego typu tokenu. Nie można zaakceptować tokeny tego typu zgodnie z bieżącymi ustawieniami zabezpieczeń.|  
|UnableToLoadCertificateIdentity|Nie można załadować tożsamości certyfikatu X.509, które są określone w konfiguracji.|  
|UnexpectedEmptyElementExpectingClaim|Określony element z określonego obszaru nazw jest pusta i nie określa prawidłowego oświadczenia tożsamości.|  
|UnknownEncodingInBinarySecurityToken|Napotkano nierozpoznane kodowanie podczas odczytu binarnego tokenu zabezpieczającego.|  
|UnsecuredMessageFaultReceived|Błąd: niezabezpieczony lub nieprawidłowo zabezpieczony została odebrana z drugiej strony. Zobacz wewnętrzny FaultException — usterek kodu i szczegóły.|  
|UnsupportedPasswordType|Token podana nazwa użytkownika ma nieobsługiwany typ hasła.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Nie można zaimportować zasad zabezpieczeń. Wymagania dotyczące ochrony dla powiązania uruchamiania bezpiecznej konwersacji nie są obsługiwane. Wymagania dotyczące ochrony dla bezpiecznej konwersacji może wymagać żądanie i odpowiedź muszą być podpisane i szyfrowane.|  
|UnsupportedSecurityPolicyAssertion|Podczas importowania zasad zabezpieczeń określone Wykryto nieobsługiwaną asercję zasad zabezpieczeń.|
