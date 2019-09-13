---
title: Token niestandardowy
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: b073375325d2989a23624303f2c40b8f61a29d02
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928656"
---
# <a name="custom-token"></a>Token niestandardowy

Ten przykład pokazuje, jak dodać implementację niestandardowego tokenu do aplikacji Windows Communication Foundation (WCF). W przykładzie zastosowano `CreditCardToken` do bezpiecznego przekazywania informacji o kartach kredytowych klienta do usługi. Token jest przekazywany w nagłówku komunikatu WS-Security i jest podpisywany i szyfrowany przy użyciu elementu symetrycznego powiązania zabezpieczeń wraz z treścią komunikatu i innymi nagłówkami komunikatów. Jest to przydatne w przypadku, gdy wbudowane tokeny nie są wystarczające. Ten przykład ilustruje sposób dostarczania niestandardowego tokenu zabezpieczającego do usługi zamiast korzystania z jednego z tokenów wbudowanych. Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

 Podsumowując, ten przykład ilustruje następujące elementy:

- Sposób przekazywania przez klienta niestandardowego tokenu zabezpieczającego do usługi.

- Jak usługa może zużywać i sprawdzać poprawność niestandardowego tokenu zabezpieczającego.

- Jak kod usługi WCF może uzyskać informacje o odebranych tokenach zabezpieczających, w tym o niestandardowym tokenie zabezpieczającym.

- Jak certyfikat X. 509 serwera jest używany do ochrony klucza symetrycznego używanego do szyfrowania i podpisywania komunikatów.

## <a name="client-authentication-using-a-custom-security-token"></a>Uwierzytelnianie klienta przy użyciu niestandardowego tokenu zabezpieczającego

 Usługa ujawnia pojedynczy punkt końcowy, który jest programowo tworzony przy `BindingHelper` użyciu `EchoServiceHost` klas i. Punkt końcowy składa się z adresu, powiązania i kontraktu. Powiązanie jest skonfigurowane z powiązaniem niestandardowym `SymmetricSecurityBindingElement` przy `HttpTransportBindingElement`użyciu i. Ten przykład ustawia, `SymmetricSecurityBindingElement` aby używać certyfikatu X. 509 usługi do ochrony klucza symetrycznego podczas transmisji i do przekazywania niestandardowego `CreditCardToken` w nagłówku komunikatu WS-Security jako podpisane i zaszyfrowane tokeny zabezpieczające. Zachowanie określa poświadczenia usługi, które mają być używane do uwierzytelniania klientów, a także informacje na temat certyfikatu usługi Service X. 509.

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        var httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        var messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 Aby korzystać z tokenu karty kredytowej w komunikacie, przykład używa niestandardowych poświadczeń usługi do zapewnienia tej funkcji. Klasa poświadczeń usługi znajduje się w `CreditCardServiceCredentials` klasie i jest dodawana do kolekcji zachowań hosta usługi `EchoServiceHost.InitializeRuntime` w metodzie.

```csharp
class EchoServiceHost : ServiceHost
{
    string creditCardFile;

    public EchoServiceHost(parameters Uri[] addresses)
        : base(typeof(EchoService), addresses)
    {
        creditCardFile = ConfigurationManager.AppSettings["creditCardFile"];
        if (string.IsNullOrEmpty(creditCardFile))
        {
            throw new ConfigurationErrorsException("creditCardFile not specified in service config");
        }

        creditCardFile = String.Format("{0}\\{1}", System.Web.Hosting.HostingEnvironment.ApplicationPhysicalPath, creditCardFile);
    }

    override protected void InitializeRuntime()
    {
        // Create a credit card service credentials and add it to the behaviors.
        CreditCardServiceCredentials serviceCredentials = new CreditCardServiceCredentials(this.creditCardFile);
        serviceCredentials.ServiceCertificate.SetCertificate("CN=localhost", StoreLocation.LocalMachine, StoreName.My);
        this.Description.Behaviors.Remove((typeof(ServiceCredentials)));
        this.Description.Behaviors.Add(serviceCredentials);

        // Register a credit card binding for the endpoint.
        Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
        this.AddServiceEndpoint(typeof(IEchoService), creditCardBinding, string.Empty);

        base.InitializeRuntime();
    }
}
```

 Punkt końcowy klienta jest konfigurowany w podobny sposób, jak punkt końcowy usługi. Klient używa tej samej `BindingHelper` klasy do utworzenia powiązania. Pozostała część instalacji znajduje się w `Client` klasie. Klient ustawia również informacje, które mają być zawarte w `CreditCardToken` i informacje o certyfikacie usługi X. 509 w kodzie Instalatora przez `CreditCardClientCredentials` dodanie wystąpienia z odpowiednimi danymi do kolekcji zachowań punktów końcowych klienta. Przykład używa certyfikatu X. 509 z nazwą podmiotu ustawioną `CN=localhost` jako certyfikat usługi.

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
var serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration.
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// Configure the credit card credentials on the channel factory.
var credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// Configure the service certificate on the credentials.
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// Replace ClientCredentials with CreditCardClientCredentials.
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine($"Echo service returned: {client.Echo()}");

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a>Implementacja niestandardowego tokenu zabezpieczającego

 Aby włączyć niestandardowy token zabezpieczający w programie WCF, Utwórz reprezentację obiektu niestandardowego tokenu zabezpieczającego. Przykład zawiera tę reprezentację w `CreditCardToken` klasie. Reprezentacja obiektu jest odpowiedzialna za przechowywanie wszystkich istotnych informacji o tokenie zabezpieczającym oraz zawiera listę kluczy zabezpieczeń zawartych w tokenie zabezpieczającym. W takim przypadku token zabezpieczający karty kredytowej nie zawiera klucza zabezpieczeń.

 W następnej sekcji opisano, co należy zrobić, aby umożliwić przesyłanie tokenów niestandardowych za pośrednictwem sieci i zużywanych przez punkt końcowy WCF.

```csharp
class CreditCardToken : SecurityToken
{
    CreditCardInfo cardInfo;
    DateTime effectiveTime = DateTime.UtcNow;
    string id;
    ReadOnlyCollection<SecurityKey> securityKeys;

    public CreditCardToken(CreditCardInfo cardInfo) : this(cardInfo, Guid.NewGuid().ToString()) { }

    public CreditCardToken(CreditCardInfo cardInfo, string id)
    {
        if (cardInfo == null)
            throw new ArgumentNullException(nameof(cardInfo));

        if (id == null)
            throw new ArgumentNullException(nameof(id));

        this.cardInfo = cardInfo;
        this.id = id;

        // The credit card token is not capable of any cryptography.
        this.securityKeys = new ReadOnlyCollection<SecurityKey>(new List<SecurityKey>());
    }

    public CreditCardInfo CardInfo { get { return this.cardInfo; } }

    public override ReadOnlyCollection<SecurityKey> SecurityKeys { get { return this.securityKeys; } }

    public override DateTime ValidFrom { get { return this.effectiveTime; } }
    public override DateTime ValidTo { get { return this.cardInfo.ExpirationDate; } }
    public override string Id { get { return this.id; } }
}
```

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Pobieranie niestandardowego tokenu karty kredytowej do i z wiadomości

 Serializatory tokenów zabezpieczających w programie WCF są odpowiedzialne za tworzenie reprezentacji obiektów tokenów zabezpieczających na podstawie kodu XML w komunikacie i Tworzenie formularza XML tokenów zabezpieczających. Są one również odpowiedzialne za inne funkcje, takie jak odczytywanie i zapisywanie identyfikatorów kluczy wskazujących tokeny zabezpieczające, ale w tym przykładzie są stosowane tylko funkcje dotyczące tokenów zabezpieczających. Aby włączyć Token niestandardowy, należy zaimplementować własny Serializator tokenu zabezpieczeń. Ten przykład używa `CreditCardSecurityTokenSerializer` klasy do tego celu.

 W usłudze, serializator niestandardowy odczytuje formę XML niestandardowego tokenu i tworzy reprezentację niestandardowego obiektu tokena.

 Na kliencie `CreditCardSecurityTokenSerializer` Klasa zapisuje informacje zawarte w reprezentacji obiektu tokenu zabezpieczającego w składniku zapisywania XML.

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null)
            throw new ArgumentNullException(nameof(reader));

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
        {
            string id = reader.GetAttribute(Constants.Id, Constants.WsUtilityNamespace);

            reader.ReadStartElement();

            // Read the credit card number.
            string creditCardNumber = reader.ReadElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace);

            // Read the expiration date.
            string expirationTimeString = reader.ReadElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace);
            DateTime expirationTime = XmlConvert.ToDateTime(expirationTimeString, XmlDateTimeSerializationMode.Utc);

            // Read the issuer of the credit card.
            string creditCardIssuer = reader.ReadElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace);
            reader.ReadEndElement();

            var cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

            return new CreditCardToken(cardInfo, id);
        }
        else
        {
            return WSSecurityTokenSerializer.DefaultInstance.ReadToken(reader, tokenResolver);
        }
    }

    protected override bool CanWriteTokenCore(SecurityToken token)
    {
        if (token is CreditCardToken)
            return true;
        return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null)
            throw new ArgumentNullException(nameof(writer));
        if (token == null)
            throw new ArgumentNullException(nameof(token));

        CreditCardToken c = token as CreditCardToken;
        if (c != null)
        {
            writer.WriteStartElement(Constants.CreditCardTokenPrefix, Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace);
            writer.WriteAttributeString(Constants.WsUtilityPrefix, Constants.Id, Constants.WsUtilityNamespace, token.Id);
            writer.WriteElementString(Constants.CreditCardNumberElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardNumber);
            writer.WriteElementString(Constants.CreditCardExpirationElementName, Constants.CreditCardTokenNamespace, XmlConvert.ToString(c.CardInfo.ExpirationDate, XmlDateTimeSerializationMode.Utc));
            writer.WriteElementString(Constants.CreditCardIssuerElementName, Constants.CreditCardTokenNamespace, c.CardInfo.CardIssuer);
            writer.WriteEndElement();
            writer.Flush();
        }
        else
        {
            base.WriteTokenCore(writer, token);
        }
    }
}
```

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Jak są tworzone klasy dostawcy tokenów i wystawców tokenów

 Poświadczenia klienta i usługi są odpowiedzialne za dostarczanie wystąpienia Menedżera tokenów zabezpieczających. Wystąpienie Menedżera tokenów zabezpieczeń służy do uzyskiwania dostawców tokenów, wystawców tokenów i serializatorów tokenów.

 Dostawca tokenów tworzy reprezentację obiektu tokenu na podstawie informacji zawartych w poświadczeniach klienta lub usługi. Reprezentacja obiektu tokenu jest następnie zapisywana w komunikacie przy użyciu serializatora tokenu (omówione w poprzedniej sekcji).

 Wystawca uwierzytelnienia tokenu sprawdza poprawność tokenów, które dotarły do wiadomości. Reprezentacja obiektu tokenu przychodzącego jest tworzona przez Serializator tokenu. Ta reprezentacja obiektu jest następnie przenoszona do uwierzytelniania tokenów w celu weryfikacji. Po pomyślnym sprawdzeniu tokenu wystawca uwierzytelnienia zwraca kolekcję `IAuthorizationPolicy` obiektów reprezentujących informacje zawarte w tokenie. Te informacje są używane później podczas przetwarzania komunikatów w celu podejmowania decyzji dotyczących autoryzacji i dostarczania oświadczeń dla aplikacji. W tym przykładzie token karty kredytowej używa `CreditCardTokenAuthorizationPolicy` do tego celu.

 Serializator tokenu jest odpowiedzialny za pobieranie obiektu reprezentacji tokenu do i z sieci. Zostało to omówione w poprzedniej sekcji.

 W tym przykładzie używamy dostawcy tokenów tylko na kliencie i uwierzytelniającego tokena tylko do usługi, ponieważ chcemy przesłać token karty kredytowej tylko w kierunku od klienta do usługi.

 Funkcje klienta znajdują się w `CreditCardClientCredentials` `CreditCardClientCredentialsSecurityTokenManager` klasach i `CreditCardTokenProvider` .

 `CreditCardServiceCredentials`W usłudze funkcje znajdują się w klasach `CreditCardTokenAuthenticator` , `CreditCardServiceCredentialsSecurityTokenManager`i `CreditCardTokenAuthorizationPolicy` .

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        public CreditCardInfo CreditCardInfo
        {
            get { return this.creditCardInfo; }
        }

        protected override ClientCredentials CloneCore()
        {
            return new CreditCardClientCredentials(this.creditCardInfo);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardClientCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardClientCredentialsSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        CreditCardClientCredentials creditCardClientCredentials;

        public CreditCardClientCredentialsSecurityTokenManager(CreditCardClientCredentials creditCardClientCredentials)
            : base (creditCardClientCredentials)
        {
            this.creditCardClientCredentials = creditCardClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // Handle this token for Custom.
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // Return server cert.
            else if (tokenRequirement is InitiatorServiceModelSecurityTokenRequirement)
            {
                if (tokenRequirement.TokenType == SecurityTokenTypes.X509Certificate)
                {
                    return new X509SecurityTokenProvider(creditCardClientCredentials.ServiceCertificate.DefaultCertificate);
                }
            }

            return base.CreateSecurityTokenProvider(tokenRequirement);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {

            return new CreditCardSecurityTokenSerializer(version);
        }

    }

    class CreditCardTokenProvider : SecurityTokenProvider
    {
        CreditCardInfo creditCardInfo;

        public CreditCardTokenProvider(CreditCardInfo creditCardInfo) : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException(nameof(creditCardInfo));

            this.creditCardInfo = creditCardInfo;
        }

        protected override SecurityToken GetTokenCore(TimeSpan timeout)
        {
            SecurityToken result = new CreditCardToken(this.creditCardInfo);
            return result;
        }
    }

    public class CreditCardServiceCredentials : ServiceCredentials
    {
        string creditCardFile;

        public CreditCardServiceCredentials(string creditCardFile)
            : base()
        {
            if (creditCardFile == null)
                throw new ArgumentNullException(nameof(creditCardFile));

            this.creditCardFile = creditCardFile;
        }

        public string CreditCardDataFile
        {
            get { return this.creditCardFile; }
        }

        protected override ServiceCredentials CloneCore()
        {
            return new CreditCardServiceCredentials(this.creditCardFile);
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new CreditCardServiceCredentialsSecurityTokenManager(this);
        }
    }

    public class CreditCardServiceCredentialsSecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        CreditCardServiceCredentials creditCardServiceCredentials;

        public CreditCardServiceCredentialsSecurityTokenManager(CreditCardServiceCredentials creditCardServiceCredentials)
            : base(creditCardServiceCredentials)
        {
            this.creditCardServiceCredentials = creditCardServiceCredentials;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
            {
                outOfBandTokenResolver = null;
                return new CreditCardTokenAuthenticator(creditCardServiceCredentials.CreditCardDataFile);
            }

            return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
        }

        public override SecurityTokenSerializer CreateSecurityTokenSerializer(SecurityTokenVersion version)
        {
            return new CreditCardSecurityTokenSerializer(version);
        }
    }

    class CreditCardTokenAuthenticator : SecurityTokenAuthenticator
    {
        string creditCardsFile;
        public CreditCardTokenAuthenticator(string creditCardsFile)
        {
            this.creditCardsFile = creditCardsFile;
        }

        protected override bool CanValidateTokenCore(SecurityToken token)
        {
            return (token is CreditCardToken);
        }

        protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateTokenCore(SecurityToken token)
        {
            CreditCardToken creditCardToken = token as CreditCardToken;

            if (creditCardToken.CardInfo.ExpirationDate < DateTime.UtcNow)
                throw new SecurityTokenValidationException("The credit card has expired.");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card.");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            var cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            var cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            var policies = new List<IAuthorizationPolicy>(1);
            policies.Add(new CreditCardTokenAuthorizationPolicy(cardClaimSet));
            return policies.AsReadOnly();
        }

        /// <summary>
        /// Helper method to check if a given credit card entry is present in the User DB
        /// </summary>
        private bool IsCardNumberAndExpirationValid(CreditCardInfo cardInfo)
        {
            try
            {
                using (var myStreamReader = new StreamReader(this.creditCardsFile))
                {
                    string line = "";
                    while ((line = myStreamReader.ReadLine()) != null)
                    {
                        string[] splitEntry = line.Split('#');
                        if (splitEntry[0] == cardInfo.CardNumber)
                        {
                            string expirationDateString = splitEntry[1].Trim();
                            DateTime expirationDateOnFile = DateTime.Parse(expirationDateString, System.Globalization.DateTimeFormatInfo.InvariantInfo, System.Globalization.DateTimeStyles.AdjustToUniversal);
                            if (cardInfo.ExpirationDate == expirationDateOnFile)
                            {
                                string issuer = splitEntry[2];
                                return issuer.Equals(cardInfo.CardIssuer, StringComparison.InvariantCultureIgnoreCase);
                            }
                            else
                            {
                                return false;
                            }
                        }
                    }
                    return false;
                }
            }
            catch (Exception e)
            {
                throw new Exception("BookStoreService: Error while retrieving credit card information from User DB " + e.ToString());
            }
        }
    }

    public class CreditCardTokenAuthorizationPolicy : IAuthorizationPolicy
    {
        string id;
        ClaimSet issuer;
        IEnumerable<ClaimSet> issuedClaimSets;

        public CreditCardTokenAuthorizationPolicy(ClaimSet issuedClaims)
        {
            if (issuedClaims == null)
                throw new ArgumentNullException(nameof(issuedClaims));
            this.issuer = issuedClaims.Issuer;
            this.issuedClaimSets = new ClaimSet[] { issuedClaims };
            this.id = Guid.NewGuid().ToString();
        }

        public ClaimSet Issuer { get { return this.issuer; } }

        public string Id { get { return this.id; } }

        public bool Evaluate(EvaluationContext context, ref object state)
        {
            foreach (ClaimSet issuance in this.issuedClaimSets)
            {
                context.AddClaimSet(this, issuance);
            }

            return true;
        }
    }
```

## <a name="displaying-the-callers-information"></a>Wyświetlanie informacji o wywołujących

 Aby wyświetlić informacje o wywołującym, użyj `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` , jak pokazano w poniższym przykładowym kodzie. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera oświadczenia autoryzacji skojarzone z bieżącym obiektem wywołującym. Oświadczenia są dostarczane przez `CreditCardToken` klasę w swojej `AuthorizationPolicies` kolekcji.

```csharp
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)
{
    claimValue = null;
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
        return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    enumerator.MoveNext();
    claimValue = (enumerator.Current.Resource == null) ? null :
        enumerator.Current.Resource.ToString();
    return true;
}

string GetCallerCreditCardNumber()
{
     foreach (ClaimSet claimSet in
         ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)
     {
         string creditCardNumber = null;
         if (TryGetStringClaimValue(claimSet,
             Constants.CreditCardNumberClaim, out creditCardNumber))
             {
                 string issuer;
                 if (!TryGetStringClaimValue(claimSet.Issuer,
                        ClaimTypes.Name, out issuer))
                 {
                     issuer = "Unknown";
                 }
                 return $"Credit card '{creditCardNumber}' issued by '{issuer}'";
        }
    }
    return "Credit card is not known";
}
```

 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.

## <a name="setup-batch-file"></a>Plik wsadowy konfiguracji

 Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji hostowanej przez usługi IIS, która wymaga zabezpieczeń opartych na certyfikatach serwera. Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.

 Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.

- Tworzenie certyfikatu serwera:

     Poniższe wiersze z `Setup.bat` pliku wsadowego tworzą certyfikat serwera do użycia. `%SERVER_NAME%` Zmienna określa nazwę serwera. Zmień tę zmienną, aby określić własną nazwę serwera. Wartość domyślna w tym pliku wsadowym to localhost. Jeśli zmienisz `%SERVER_NAME%` zmienną, musisz przejść przez pliki Client.cs i Service.cs i zamienić wszystkie wystąpienia localhost na nazwę serwera używaną w skrypcie Setup. bat.

     Certyfikat jest przechowywany w magazynie `LocalMachine` (Personal) w lokalizacji magazynu. Certyfikat jest przechowywany w magazynie LocalMachine dla usług hostowanych przez usługi IIS. W przypadku usług samodzielnych należy zmodyfikować plik wsadowy, aby przechowywać certyfikat klienta w lokalizacji magazynu CurrentUser przez zastąpienie ciągu LocalMachine ciągiem CurrentUser.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta:

     Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta. Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta. Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.

    ```bat
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Aby umożliwić dostęp do klucza prywatnego certyfikatu z usługi hostowanej przez usługi IIS, konto użytkownika, pod którym działa proces hostowany przez usługi IIS, musi mieć przyznane odpowiednie uprawnienia do klucza prywatnego. Jest to realizowane przez ostatnie kroki skryptu Setup. bat.

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012. Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.

#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1. Otwórz okno wiersza polecenia programu Visual Studio 2012 z uprawnieniami administratora i uruchom setup. bat z przykładowego folderu instalacji. Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert. exe.

> [!NOTE]
> Pamiętaj o usunięciu certyfikatów, uruchamiając Oczyść. bat po zakończeniu z przykładem. Inne przykłady zabezpieczeń używają tych samych certyfikatów.  
  
1. Uruchom plik Client. exe z katalogu client\bin. Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.  
  
2. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computer"></a>Aby uruchomić przykład na komputerze  
  
1. Utwórz katalog na komputerze usługi dla plików binarnych usługi.  
  
2. Skopiuj pliki programu Service Files do katalogu usługi na komputerze usługi. Nie zapomnij skopiować CreditCardFile. txt; w przeciwnym razie wystawca uwierzytelnienia karty kredytowej nie może zweryfikować informacji o karcie kredytowej wysłanych przez klienta. Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.  
  
3. Musisz mieć certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera. Można go utworzyć przy użyciu Setup. bat, jeśli zmienisz `%SERVER_NAME%` zmienną na w pełni kwalifikowaną nazwę komputera, na którym usługa jest hostowana. Należy pamiętać, że plik Setup. bat musi być uruchamiany w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.  
  
4. Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople na kliencie. Należy to zrobić tylko wtedy, gdy certyfikat serwera nie zostanie wystawiony przez zaufanego wystawcy.  
  
5. W pliku EchoServiceHost.cs Zmień wartość w polu Nazwa podmiotu certyfikatu, aby określić w pełni kwalifikowaną nazwę komputera zamiast localhost.  
  
6. Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.  
  
7. W pliku Client.cs Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.  
  
8. W pliku Client.cs Zmień nazwę podmiotu certyfikatu X. 509 usługi w taki sposób, aby była zgodna z w pełni kwalifikowaną nazwą komputera hosta zdalnego zamiast localhost.  
  
9. Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po przykładzie  
  
1. Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.  
