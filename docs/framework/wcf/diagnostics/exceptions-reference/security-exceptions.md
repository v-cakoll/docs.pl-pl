---
title: Wyjątki zabezpieczeń
ms.date: 03/30/2017
ms.assetid: 76d5e5cd-e4f4-404f-9a5a-ec3522494ad8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 057d01ba918a41df0bdf2acc30c9bb35777ebc27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-exceptions"></a>Wyjątki zabezpieczeń
W tym temacie wymieniono wszystkie wyjątki zabezpieczeń.  
  
## <a name="exception-list"></a>Listy wyjątków  
  
|Kod zasobu|Ciąg zasobu|  
|-------------------|---------------------|  
|AnonymousLogonsAreNotAllowed|Usługi nie umożliwiają anonimowego logowania.|  
|AtLeastOneContractOperationRequestRequiresProtectionLevelNotSupportedByBinding|Komunikat żądania musi być chroniony. Jest to wymagane przez operację określonego kontraktu. Ochronę musi zapewniać określonego powiązania.|  
|AtLeastOneContractOperationResponseRequiresProtectionLevelNotSupportedByBinding|Komunikat odpowiedzi musi być chroniony. Jest to wymagane przez operację określonego kontraktu. Ochronę musi zapewniać określonego powiązania.|  
|AtMostOnePrimarySignatureInReceiveSecurityHeader|W nagłówku zabezpieczeń jest dozwolony tylko jeden podpis podstawowy.|  
|BadContextTokenFaultReason|Token kontekstu zabezpieczeń wygasł lub jest nieprawidłowy. Wiadomość nie została przetworzona.|  
|BadEncryptionState|Element EncryptedData lub EncryptedKey jest w nieprawidłowym stanie dla tej operacji.|  
|BasicHttpMessageSecurityRequiresCertificate|Powiązanie BasicHttp wymaga BasicHttpBinding.Security.Message.ClientCredentialType odpowiadał do poświadczeń BasicHttpMessageCredentialType.Certificate dla bezpiecznych wiadomości. Wybierz opcję zabezpieczeń Transport lub TransportWithMessageCredential dla poświadczeń UserName.|  
|BasicTokenCannotBeWrittenWithoutEncryption|Token podstawowy nie można zapisać bez szyfrowania.|  
|BindingDoesNotSupportProtectionForRst|Określone powiązanie dla określonego kontraktu jest skonfigurowana z SecureConversation, ale tryb uwierzytelniania nie jest zapewnienie oparte na żądanie/odpowiedź integralności i poufności wymaganej dla negocjacji.|  
|BindingDoesNotSupportWindowsIdenityForImpersonation|Operacja kontraktu określonego wymaga tożsamości systemu Windows dla automatycznej personifikacji. Nie podano tożsamości systemu Windows reprezentująca procedurę wywołującą przez określone powiązanie dla określonego kontraktu.|  
|CachedNegotiationStateQuotaReached|Usługa nie może buforować stanu negocjacji, ponieważ osiągnięto określonej pojemności. Ponów żądanie.|  
|CacheQuotaReached|Nie można dodać elementu. Maksymalny rozmiar buforu został określony.|  
|CannotDetermineSPNBasedOnAddress|Klient nie może określić głównej nazwy usługi na podstawie tożsamości z adresu docelowego określony na potrzeby SspiNegotiation/Kerberos. Tożsamość adresu docelowego musi być tożsamością UPN (jak acmedomain\\\alice) lub tożsamością SPN (jak host/komputer1).|  
|CannotFindCert|Nie można odnaleźć certyfikatu X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue.|  
|CannotFindCertForTarget|Nie można odnaleźć certyfikatu X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue dla określonego celu.|  
|CannotFindCorrelationStateForApplyingSecurity|Nie można odnaleźć stanu korelacji do zastosowania zabezpieczeń na udzielenie odpowiedzi na odpowiadający.|  
|CannotFindNegotiationState|Nie można odnaleźć stanu negocjacji dla określonego kontekstu.|  
|CannotFindSecuritySession|Nie można odnaleźć sesji zabezpieczeń o określonym identyfikatorze.|  
|CannotImportProtectionLevelForContract|Zasady importu procesu nie można zaimportować powiązania dla określonej kontraktu. Wymagania dotyczące ochrony dla powiązania nie są zgodne z powiązaniem już importowane dla kontraktu. Należy ponownie skonfigurować powiązanie.|  
|CannotImportSupportingTokensForOperationWithoutRequestAction|Nie można zaimportować zasad zabezpieczeń. Zasady zabezpieczeń zawierają wymagania tokenu pomocniczego w zakresie operacji. Opis kontraktu nie określa akcji dla komunikatu żądania skojarzonego z tą operacją.|  
|CannotIssueRstTokenType|Nie można wystawić tokenu lub określonego typu.|  
|CannotObtainIssuedTokenKeySize|Nie można określić rozmiaru klucza wystawionego tokenu.|  
|CannotPerformImpersonationOnUsernameToken|Personifikacja przy użyciu tokenu klienta nie jest możliwe. Określone powiązanie dla określonego kontraktu używa tokenu zabezpieczeń nazwy użytkownika do uwierzytelniania klientów z dostawcę członkostwa w zarejestrowany. Użyj innego typu tokenu zabezpieczającego dla klienta.|  
|CannotPerformS4UImpersonationOnPlatform|Określony powiązania dla określonej kontraktu obsługuje personifikację tylko w [!INCLUDE[ws2003](../../../../../includes/ws2003-md.md)] i w nowszych wersjach systemu Windows. Użyj uwierzytelniania SspiNegotiated i powiązania z Secure Conversation z włączonym anulowaniem.|  
|CannotReadKeyIdentifier|Nie można odczytać KeyIdentifier z określonego elementu z określonego obszaru nazw.|  
|CannotReadToken|Nie można odczytać tokenu z określonego elementu z określonego obszaru nazw dla elementu BinarySecretSecurityToken, z określonym ValueType. Jeśli ten element powinien być prawidłowy, upewnij się, że skonfigurowano zabezpieczeń, aby obsługiwały tokeny o nazwie, określić typ przestrzeni nazw i wartości.|  
|CertificateUnsupportedForHttpTransportCredentialOnly|Uwierzytelnianie klienta oparte na certyfikatach jest nieobsługiwane w trybie zabezpieczeń TransportCredentialOnly. Wybierz tryb zabezpieczeń Transport.|  
|ClaimTypeCannotBeEmpty|Element claimType nie może być pustym ciągiem.|  
|ClientCertificateNotProvided|Nie dostarczono certyfikatu klienta. Certyfikat można ustawić na ClientCredentials lub ServiceCredentials.|  
|ClientCredentialTypeMustBeSpecifiedForMixedMode|Wartość ClientCredentialType.None jest nieprawidłowa dla trybu zabezpieczeń TransportWithMessageCredential. Określ typ poświadczeń lub użyj innego trybu zabezpieczeń.|  
|ConfigurationSchemaInsuffientForSecurityBindingElementInstance|Schemat konfiguracji jest niewystarczający do opisania niestandardowej konfiguracji następującego elementu powiązania zabezpieczeń:|  
|DerivedKeyTokenGenerationAndLengthTooHigh|W przesunięcie wyprowadzenia klucza większe niż maksymalne dozwolone przesunięcie klucza pochodnego określony wynik generowania i długości.|  
|DnsIdentityCheckFailedForIncomingMessage|Nie można sprawdzić tożsamości komunikatu przychodzącego. Określono tożsamości domeny oczekiwanej nazwy systemu (nazw domen DNS) zdalnego punktu końcowego. Zdalny punkt końcowy udostępnił, oświadczenie określonej domeny system nazw (domen DNS). Jeśli jest to uprawniony zdalny punkt końcowy, można naprawić ten problem, określając tożsamość systemu nazw domen jako właściwość identity elementu EndpointAddress podczas tworzenia kanału proxy.|  
|DnsIdentityCheckFailedForOutgoingMessage|Nie można sprawdzić tożsamości wiadomości, który został przejście. Zdalny punkt końcowy powinny mieć tożsamości systemu nazwy określonej domeny. Zdalny punkt końcowy udostępnił, oświadczenie system nazw domen (DNS). Jeśli jest to uprawniony zdalny punkt końcowy, można rozwiązać problem, jawnie ustawiając tożsamość DNS jako właściwość Identity elementu EndpointAddress podczas tworzenia kanału proxy.|  
|DuplicateIdInMessageToBeVerified|Określony identyfikator pojawił się dwukrotnie w komunikacie dostarczonym do weryfikacji.|  
|EmptyBase64Attribute|Znaleziono pustą wartość dla wymaganego atrybutu base-64 nazwy i przestrzeni nazw.|  
|ExportOfBindingWithAsymmetricAndTransportSecurityNotSupported|Eksport zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element AsymmetricSecurityBindingElement i element wiązania bezpiecznego transportu. Eksportowanie zasad dla takiego powiązania nie jest obsługiwane.|  
|ExportOfBindingWithSymmetricAndTransportSecurityNotSupported|Eksport zasad zabezpieczeń nie powiodło się. Powiązanie zawiera element SymmetricSecurityBindingElement i element wiązania bezpiecznego transportu. Eksportowanie zasad dla takiego powiązania nie jest obsługiwane.|  
|ExportOfBindingWithTransportSecurityBindingElementAndNoTransportSecurityNotSupported|Eksport zasad zabezpieczeń nie powiodło się. Wiązanie zawiera TransportSecurityBindingElement, ale żaden element powiązania transportu implementującego ITransportTokenAssertionProvider. Eksportowanie zasad dla takiego powiązania nie jest obsługiwane. Upewnij się, że w powiązaniu elementu powiązania transportu implementuje interfejs ITransportTokenAssertionProvider.|  
|FoundMultipleCerts|Znaleziono wiele certyfikatów X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue. Podaj dokładniejszą wartość wyszukiwania.|  
|FoundMultipleCertsForTarget|Znaleziono wiele certyfikatów X.509 przy użyciu określonych kryteriów wyszukiwania: StoreName, StoreLocation, FindType, FindValue dla określonego celu. Podaj dokładniejszą wartość wyszukiwania.|  
|HeaderDecryptionNotSupportedInWsSecurityJan2004|Element SecurityVersion.WSSecurityJan2004 nie obsługuje odszyfrowywania nagłówków. Użyj SecurityVersion.WsSecurityXXX2005 lub nowszego albo zabezpieczeń transportu, aby zaszyfrować cały komunikat.|  
|IdentityCheckFailedForIncomingMessage|Nie można sprawdzić tożsamości komunikatu przychodzącego. Oczekiwana tożsamość jest określana dla docelowego punktu końcowego.|  
|IdentityCheckFailedForOutgoingMessage|Nie można sprawdzić tożsamości komunikatu wychodzącego. Oczekiwana tożsamość jest określana dla docelowego punktu końcowego.|  
|IncorrectSpnOrUpnSpecified|Uwierzytelnianie interfejsu dostawcy obsługi (SSPI) zabezpieczeń nie powiodło się. Serwer nie może działać na koncie o określonej tożsamości. Jeśli serwer działa na koncie usługi (na przykład usługi sieciowej), określ element ServicePrincipalName konta jako tożsamość w elemencie EndpointAddress serwera. Jeśli serwer działa na koncie użytkownika, określ element UserPrincipalName konta jako tożsamość w elemencie EndpointAddress serwera.|  
|InvalidAttributeInSignedHeader|Określony nagłówek podpisem zawiera określony atrybut. Oczekiwany atrybut został określony.|  
|InvalidCloseResponseAction|Odpowiedź o zamknięciu sesji zabezpieczeń została odebrana z określoną akcję nieprawidłowy.|  
|InvalidQName|Nazwa QName jest nieprawidłowy.|  
|InvalidRenewResponseAction|Odnowioną odpowiedź sesji zabezpieczeń została odebrana z określoną akcję nieprawidłowy.|  
|InvalidSspiNegotiation|Negocjowanie interfejsu dostawcy obsługi zabezpieczeń nie powiodło się.|  
|IssuerBindingNotPresentInTokenRequirement|Menedżer tokenów zabezpieczających wymaga określenia elementu powiązania zabezpieczeń dla uruchamiania, należy określić wymaganie tokenu, który opisuje bezpiecznej konwersacji. Wymóg tokenu jest następujący:|  
|KeyLengthMustBeMultipleOfEight|Określona długość klucza nie jest wielokrotnością liczby 8 dla kluczy symetrycznych.|  
|LsaAuthorityNotContacted|Błąd wewnętrzny protokołu SSL (zobacz kod stanu Win32, aby uzyskać szczegółowe informacje). Sprawdź certyfikat serwera, aby ustalić, czy jest zdolny do wymiany klucza.|  
|MaximumPolicyRedirectionsExceeded|Osiągnięto limit cyklicznego pobierania zasad. Sprawdź, czy istnieje pętla w łańcuchu usług federacyjnych.|  
|MessagePartSpecificationMustBeImmutable|Specyfikacja części wiadomości musi być stała, zanim zostanie ustawiona.|  
|MissingCustomCertificateValidator|Element X509CertificateValidationMode.Custom wymaga CustomCertificateValidator. Określ właściwość CustomCertificateValidator.|  
|MissingCustomUserNamePasswordValidator|Element UserNamePasswordValidationMode.Custom wymaga CustomUserNamePasswordValidator. Określ właściwość CustomUserNamePasswordValidator.|  
|MissingMembershipProvider|Element UserNamePasswordValidationMode.MembershipProvider wymaga MembershipProvider. Określ właściwość MembershipProvider.|  
|NoBinaryNegoToSend|Nie negocjacji binarnej zostało wysłane do drugiej strony.|  
|NoEncryptionPartsSpecified|Nie części komunikatów szyfrowania zostały określone dla komunikatów z określonej akcji.|  
|NoKeyInfoInEncryptedItemToFindDecryptingToken|Nie znaleziono wartości KeyInfo w zaszyfrowanym elemencie, aby znaleźć odszyfrowywania tokenu.|  
|NonceLengthTooShort|Określony identyfikator jednorazowy jest zbyt krótki. Minimalna wymagana długość identyfikatora jednorazowego wynosi 4 bajty.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheck|Nie wychodzący adres EndpointAddress jest dostępne sprawdzić tożsamość wiadomości do wysłania.|  
|NoOutgoingEndpointAddressAvailableForDoingIdentityCheckOnReply|Nie wychodzący adres EndpointAddress jest dostępna, można sprawdzić tożsamość odebranej odpowiedzi.|  
|NoPartsOfMessageMatchedPartsToSign|Podpis nie został utworzony, ponieważ żadna część wiadomości dopasowane dostarczoną specyfikacją części wiadomości.|  
|NoPrincipalSpecifiedInAuthorizationContext|Określono nie niestandardowego podmiotu w kontekście autoryzacji.|  
|NoSignatureAvailableInSecurityHeaderToDoReplayDetection|Podpis nie jest dostępna w nagłówku zabezpieczeń, aby dostarczyć identyfikator jednorazowy na potrzeby wykrywania powtarzania.|  
|NoSignaturePartsSpecified|Żadnych części podpisu wiadomości zostały określone dla komunikatów z określonej akcji.|  
|NoSigningTokenAvailableToDoIncomingIdentityCheck|Nie podpisywania tokenu jest dostępny dla przychodzących sprawdzanie tożsamości.|  
|NoTimestampAvailableInSecurityHeaderToDoReplayDetection|Brak sygnatury czasowej jest dostępna w nagłówku zabezpieczeń do przeprowadzenia wykrywania powtarzania.|  
|NoTransportTokenAssertionProvided|Nie można wyeksportować zasad zabezpieczeń. Dostarczone potwierdzenie tokenu transportu typu innego niż podany nie utworzyło potwierdzenia tokenu transportu do dołączenia potwierdzenia zasad zabezpieczeń SP: TransportBinding.|  
|OnlyOneOfEncryptedKeyOrSymmetricBindingCanBeSelected|Symetryczny protokół zabezpieczeń może być skonfigurowany z dostawcy tokenu symetrycznego i wystawcy uwierzytelnienia tokenu symetrycznego lub pomocą asymetrycznego dostawcy tokenu. Nie można skonfigurować zarówno.|  
|OperationCannotBeDoneOnReceiverSideSecurityHeaders|Nie można wykonać tej operacji na nagłówkach zabezpieczeń odbiornika.|  
|OperationDoesNotAllowImpersonation|Operacji określonej usługi, która należy do kontraktu o określonej nazwie i przestrzeni nazw nie zezwala na personifikację.|  
|PolicyRequiresConfidentialityWithoutIntegrity|Zasada zabezpieczeń wiadomości dla określonej akcji wymaga poufności bez integralności. Poufność bez integralności nie jest obsługiwana.|  
|PrimarySignatureIsRequiredToBeEncrypted|Podpis podstawowy musi być zaszyfrowany.|  
|PropertySettingErrorOnProtocolFactory|Wymagana właściwość fabrykę protokołów zabezpieczeń określonej nie jest ustawiona lub ma nieprawidłową wartość.|  
|ProtocolFactoryCouldNotCreateProtocol|Fabryka protokołów nie może utworzyć protokołu.|  
|PublicKeyNotRSA|Klucz publiczny nie jest kluczem RSA.|  
|RequiredMessagePartNotEncrypted|Część wiadomości wymagana określona nie została zaszyfrowana.|  
|RequiredMessagePartNotEncryptedNs|Część wiadomości wymagana określona nie została zaszyfrowana.|  
|RequiredMessagePartNotSigned|Część wiadomości wymagana określona nie został podpisany.|  
|RequiredMessagePartNotSignedNs|Część wiadomości wymagana określona nie został podpisany.|  
|RequiredSecurityHeaderElementNotSigned|Element nagłówka zabezpieczeń określonej o określonym identyfikatorze muszą być podpisane.|  
|RequiredSecurityTokenNotEncrypted|Określony "tokenu zabezpieczającego z trybem załączników określonego muszą być szyfrowane.|  
|RequiredSecurityTokenNotSigned|Musi być podpisany token zabezpieczający określonego z trybem załączników określony.|  
|RequiredSignatureMissing|Podpis musi być w nagłówku zabezpieczeń.|  
|RequireNonCookieMode|Określone powiązanie z określonego obszaru nazw jest skonfigurowany do wystawiania tokenów kontekstów zabezpieczeń plików cookie. Usługi integracji COM + nie obsługują tokenów kontekstów zabezpieczeń plików cookie.|  
|RevertingPrivilegeFailed|Operacja odwracania nie powiodła się z określonym wyjątkiem.|  
|RSTRAuthenticatorIncorrect|Właściwość combinedhash elementu RequestSecurityTokenResponse jest niepoprawna.|  
|SecureConversationCancelNotAllowedFaultReason|Anulowanie bezpiecznej konwersacji nie jest dozwolona przez powiązanie.|  
|SecureConversationDriverVersionDoesNotSupportSession|Skonfigurowana wersja mechanizmu SecureConversation nie obsługuje sesji. Użyj wersji WSSecureConversationFeb2005 lub nowszej.|  
|SecureConversationRequiredByReliableSession|Nie można utworzyć niezawodnej sesji bez bezpiecznej konwersacji. Włącz obsługę bezpiecznej konwersacji.|  
|SecurityAuditFailToLoadDll|Nie można załadować określonej biblioteki dołączanej dynamicznie (dll).|  
|SecurityAuditNotSupportedOnChannelFactory|Element SecurityAuditBehavior nie jest obsługiwany w fabryce kanałów.|  
|SecurityAuditPlatformNotSupported|Bieżąca platforma nie jest obsługiwana zapisywania komunikatów inspekcji do dziennika zabezpieczeń. Komunikaty inspekcji należy zapisywać do dziennika aplikacji.|  
|SecurityBindingElementCannotBeExpressedInConfig|Nie zaimportowano zasadę zabezpieczeń dla punktu końcowego. Zasada zabezpieczeń zawiera wymagania, których nie można przedstawić w konfiguracji systemu Windows Communication Foundation. Poszukaj komentarza dotyczącego parametrów SecurityBindingElement wymaganych w wygenerowanym pliku konfiguracji. Utwórz poprawny element powiązania z kodem. Konfiguracja powiązania, który znajduje się w pliku konfiguracji nie jest bezpieczne.|  
|SecurityBindingSupportsOneWayOnly|SecurityBinding dla określonego powiązania dla określonej kontraktu obsługuje tylko operację OneWay.|  
|SecurityContextDoesNotAllowImpersonation|Nie można rozpocząć personalizacji, ponieważ element SecurityContext dla roli UltimateReceiver z komunikatu żądania z określonej akcji nie jest mapowany na tożsamość systemu Windows.|  
|SecurityListenerClosing|Odbiornik nie przyjmuje nowych bezpiecznych konwersacji, ponieważ trwa jego zamykanie.|  
|SecurityListenerClosingFaultReason|Serwer nie akceptuje obecnie nowych bezpiecznych konwersacji, ponieważ trwa jego zamykanie. Spróbuj ponownie później.|  
|SecurityProtocolFactoryShouldBeSetBeforeThisOperation|Fabryka protokołów zabezpieczeń musi być ustawiona przed wykonaniem tej operacji.|  
|SecuritySessionAbortedFaultReason|Sesja zabezpieczeń została przerwana. Może to być, ponieważ nie otrzymano żadnych wiadomości w sesji zbyt długo.|  
|SecuritySessionKeyIsStale|Należy odnowić klucz sesji przed użyciem go do zabezpieczania komunikatów aplikacji.|  
|SecuritySessionLimitReached|Nie można utworzyć sesji zabezpieczeń. Spróbuj ponownie później.|  
|SecuritySessionNotPending|Trwa oczekiwanie na żadna sesja zabezpieczeń o określonym identyfikatorze.|  
|SecurityTokenParametersHasIncompatibleInclusionMode|Określone powiązanie jest skonfigurowane z parametrem tokenu zabezpieczającego, który ma określony zabezpieczeń niezgodny tryb dołączania tokenu. Określ tryb dołączania tokenu zabezpieczającego alternatywny.|  
|SecurityVersionDoesNotSupportEncryptedKeyBinding|Określone powiązanie dla określonego kontraktu została skonfigurowana z niezgodną wersją zabezpieczeń, który nie obsługuje niedołączonych odwołań do elementów EncryptedKey. Użyj określonej wartości lub wyższej jako wersji zabezpieczeń dla powiązania.|  
|SecurityVersionDoesNotSupportSignatureConfirmation|Określony element SecurityVersion nie obsługuje potwierdzenia podpisu. Użyj nowszego elementu SecurityVersion.|  
|SecurityVersionDoesNotSupportThumbprintX509KeyIdentifierClause|Określone powiązanie dla określonego kontraktu jest skonfigurowany z wersją zabezpieczeń, która nie obsługuje zewnętrznych odwołań do tokenów X.509 z użyciem wartości odcisku palca certyfikatu. Użyj określonej wartości lub wyższej jako wersji zabezpieczeń dla powiązania.|  
|SenderSideSupportingTokensMustSpecifySecurityTokenParameters|Parametry tokenu zabezpieczającego musi być określone z tokenami pomocniczymi dla każdego komunikatu.|  
|ServerCertificateNotProvided|Odbiorca nie przedstawił swojego certyfikatu. Ten certyfikat jest wymagany przez protokół TLS. Obie strony muszą mieć dostęp do swoich certyfikatów.|  
|SignatureConfirmationNotSupported|Skonfigurowana wersja SecurityVersion nie obsługuje potwierdzenia podpisu. Użyj WSSecurityXXX2005 lub nowszej.|  
|SignatureConfirmationRequiresRequestReply|Fabryka protokołu musi obsługiwać zabezpieczenia żądanie/odpowiedź, aby oferować potwierdzenie podpisu.|  
|SignatureNotExpected|Podpis nie jest oczekiwany dla tego komunikatu.|  
|SigningTokenHasNoKeys|Określony token podpisujący nie ma kluczy. Token zabezpieczający jest używany w kontekście, który wymaga wykonywania operacji kryptograficznych, ale token nie zawiera kluczy kryptograficznych. Typ tokenu nie obsługuje operacji kryptograficznych, albo konkretne wystąpienie tokenu nie zawiera kluczy kryptograficznych. Sprawdź konfigurację upewnij się, że typy tokenów (na przykład UserNameSecurityToken) nie są określane w kontekście wymagającym operacji kryptograficznych (na przykład tokenu pomocniczego).|  
|SpnegoImpersonationLevelCannotBeSetToNone|Interfejs dostawcy obsługi zabezpieczeń nie obsługuje personifikacji poziomu "Brak". Określ poziom Identyfikacja, personifikacja lub delegowanie.|  
|SslClientCertMustHavePrivateKey|Określony certyfikat musi mieć klucz prywatny. Proces musi mieć prawa dostępu do klucza prywatnego.|  
|SslServerCertMustDoKeyExchange|Określony certyfikat musi mieć klucz prywatny, który jest zdolny do wymiany klucza. Proces musi mieć prawa dostępu do klucza prywatnego.|  
|StandardsManagerCannotWriteObject|Serializator tokenów nie można rozszeregować określonego obiektu.  Jeśli jest to typ niestandardowy, należy użyć serializatora niestandardowego.|  
|TimeStampHasCreationAheadOfExpiry|Sygnatura czasowa zabezpieczeń jest nieprawidłowy, ponieważ jej godzina utworzenia jest większa lub równa godzinie wygaśnięcia.|  
|TimeStampHasCreationTimeInFuture|Sygnatura czasowa zabezpieczeń jest nieprawidłowy, ponieważ jej godzina utworzenia przypada w przyszłości. Bieżący czas jest określona, a dopuszczalna niedokładność zegara jest określona.|  
|TimeStampHasExpiryTimeInPast|Sygnatura czasowa zabezpieczeń jest nieodświeżona, ponieważ jego czas wygaśnięcia jest w przeszłości. Bieżący czas jest określona, a dopuszczalna niedokładność zegara jest określona.|  
|TimeStampWasCreatedTooLongAgo|Sygnatura czasowa zabezpieczeń jest nieodświeżona, ponieważ jej godzina utworzenia jest zbyt daleko w przeszłości. Bieżący czas, okres istnienia sygnatury czasowej maksymalna, a dopuszczalna niedokładność zegara zostały określone.|  
|TokenProviderCannotGetTokensForTarget|Dostawca tokenu nie można uzyskać tokenów dla określonego celu.|  
|TooManyIssuedSecurityTokenParameters|Pewien etap stowarzyszonego łańcucha zabezpieczeń zawiera wiele parametrów IssuedSecurityTokenParameters. InfoCard system obsługuje tylko jeden element IssuedSecurityTokenParameters dla każdego etapu.|  
|TransportDoesNotProtectMessage|Określone powiązanie dla określonego kontraktu jest skonfigurowany z trybu uwierzytelniania wymagającego integralności poziomu transportu i poufności. Jednak transportu nie może zapewnić integralności i poufności.|  
|TrustApr2004DoesNotSupportCertainIssuedTokens|Wersja WSTrustApr2004 nie obsługuje wystawiania certyfikatów X.509 ani elementów EncryptedKey. Skorzystaj z wersji WsTrustFeb2005 lub nowszej.|  
|TrustDriverVersionDoesNotSupportSession|Skonfigurowana wersja zaufania nie obsługuje sesji. Skorzystaj z wersji WSTrustFeb2005 lub nowszej.|  
|UnableToCreateICryptoFromTokenForSignatureVerification|Nie można utworzyć interfejsu ICrypto na z określonym tokenem weryfikacji podpisu.|  
|UnableToCreateSymmetricAlgorithmFromToken|Nie można utworzyć określonego algorytmu symetrycznego w tokenie.|  
|UnableToDeriveKeyFromKeyInfoClause|Określony klauzuli KeyInfo rozpoznać z określonym tokenem, który nie zawiera klucza symetrycznego, który może służyć do wyprowadzenia.|  
|UnableToFindTokenAuthenticator|Nie można odnaleźć wystawcy uwierzytelnienia tokenu dla określonego typu tokenu. Nie można zaakceptować tokeny tego typu zgodnie z bieżącymi ustawieniami zabezpieczeń.|  
|UnableToLoadCertificateIdentity|Nie można załadować tożsamości certyfikatu X.509 określonej w konfiguracji.|  
|UnexpectedEmptyElementExpectingClaim|Określony element z określonego obszaru nazw jest pusta i nie określa prawidłowego oświadczenia tożsamości.|  
|UnknownEncodingInBinarySecurityToken|Napotkano nierozpoznane kodowanie wystąpił podczas odczytu binarnego tokenu zabezpieczającego.|  
|UnsecuredMessageFaultReceived|Niezabezpieczony lub nieprawidłowo zabezpieczony błąd została odebrana od drugiej strony. Można znaleźć w wewnętrznym wyjątku FaultException kod i szczegóły.|  
|UnsupportedPasswordType|Token określona nazwa użytkownika ma nieobsługiwany typ hasła.|  
|UnsupportedSecureConversationBootstrapProtectionRequirements|Nie można zaimportować zasad zabezpieczeń. Wymagania dotyczące ochrony ładowania początkowego powiązania bezpiecznej konwersacji nie są obsługiwane. Wymaganiami zabezpieczeń dotyczącymi uruchomienia początkowego bezpiecznej konwersacji może wymagać zarówno żądanie, jak i odpowiedź muszą być podpisane i zaszyfrowane.|  
|UnsupportedSecurityPolicyAssertion|Podczas importowania zasad zabezpieczeń określonej Wykryto nieobsługiwane potwierdzenie zasad zabezpieczeń.|
