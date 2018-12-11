---
title: Token niestandardowy
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 8aa41a1f9651d0a385836178bc791c14706c17e4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243052"
---
# <a name="custom-token"></a>Token niestandardowy
Niniejszy przykład pokazuje, jak dodać niestandardową implementację tokenu w aplikacji Windows Communication Foundation (WCF). W przykładzie użyto `CreditCardToken` można bezpiecznie przekazać informacje o kartach kredytowych klienta do usługi. Token jest przekazywany w nagłówku wiadomości WS-Security jest podpisany i szyfrowane przy użyciu elementu powiązania zabezpieczeń symetryczne, wraz z treści wiadomości i innych nagłówków wiadomości. Jest to przydatne w przypadkach, gdzie wbudowany tokenów nie są wystarczające. W tym przykładzie pokazano, jak zapewnić tokenu zabezpieczającego niestandardowe z usługą zamiast przy użyciu jednej z wbudowanych tokenów. Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".

> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

 Aby podsumować, w przykładzie pokazano poniżej:

-   Jak klient może przekazać token zabezpieczający niestandardowego do usługi.

-   Jak usługa korzystać i sprawdzanie poprawności tokenu zabezpieczającego niestandardowych.

-   Jak kod usługi WCF można uzyskać informacje na temat tokenów zabezpieczających odebrane, wraz z tokenem zabezpieczeń niestandardowych.

-   Jak certyfikat X.509 umożliwia ochronę klucz symetryczny, używany do szyfrowania wiadomości i podpis.

## <a name="client-authentication-using-a-custom-security-token"></a>Uwierzytelnianie klienta przy użyciu tokenu zabezpieczającego niestandardowe
 Usługa udostępnia pojedynczy punkt końcowy, który programowo jest tworzony przy użyciu `BindingHelper` i `EchoServiceHost` klasy. Punkt końcowy składa się z adresu, powiązanie i kontrakt. Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`. W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikatu X.509 usługi ochrony klucza symetrycznego podczas przesyłania i przekazać niestandardową `CreditCardToken` w nagłówku wiadomości WS-Security jako token zabezpieczający podpisane i zaszyfrowane. Zachowanie Określa poświadczenia usługi, które mają być używane do uwierzytelniania klienta, a także informacje o certyfikacie X.509.

```csharp
public static class BindingHelper
{
    public static Binding CreateCreditCardBinding()
    {
        HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

        // The message security binding element will be configured to require a credit card.
        // The token that is encrypted with the service's certificate.
        SymmetricSecurityBindingElement messageSecurity = new SymmetricSecurityBindingElement();
        messageSecurity.EndpointSupportingTokenParameters.SignedEncrypted.Add(new CreditCardTokenParameters());
        X509SecurityTokenParameters x509ProtectionParameters = new X509SecurityTokenParameters();
        x509ProtectionParameters.InclusionMode = SecurityTokenInclusionMode.Never;
        messageSecurity.ProtectionTokenParameters = x509ProtectionParameters;
        return new CustomBinding(messageSecurity, httpTransport);
    }
}
```

 Korzystanie z kartą kredytową tokenu w wiadomości, w przykładzie użyto niestandardowego poświadczenia do tej funkcji. Klasa poświadczenia usługi znajduje się w `CreditCardServiceCredentials` klasy i jest dodawany do kolekcji zachowań usługi hosta w `EchoServiceHost.InitializeRuntime` metody.

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

 Punkt końcowy klienta skonfigurowano w podobny sposób jak punkt końcowy usługi. Klient używa tych samych `BindingHelper` klasy, aby utworzyć powiązanie. Pozostała konfiguracja zostanie znajduje się w `Client` klasy. Klient ustawia również informacje zawarte w `CreditCardToken` i informacji o certyfikacie X.509 usługi w kodzie Instalatora, dodając `CreditCardClientCredentials` wystąpienia odpowiednie dane do kolekcji zachowań punktu końcowego klienta. W przykładzie użyto certyfikatu X.509 z nazwą podmiotu równa `CN=localhost` jako certyfikat usługi.

```csharp
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");

// Create a client with given client endpoint configuration
channelFactory = new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);

// configure the credit card credentials on the channel factory
CreditCardClientCredentials credentials =
      new CreditCardClientCredentials(
      new CreditCardInfo(creditCardNumber, issuer, expirationTime));
// configure the service certificate on the credentials
credentials.ServiceCertificate.SetDefaultCertificate(
      "CN=localhost", StoreLocation.LocalMachine, StoreName.My);

// replace ClientCredentials with CreditCardClientCredentials
channelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
channelFactory.Endpoint.Behaviors.Add(credentials);

client = channelFactory.CreateChannel();

Console.WriteLine("Echo service returned: {0}", client.Echo());

((IChannel)client).Close();
channelFactory.Close();
```

## <a name="custom-security-token-implementation"></a>Implementacja tokenu zabezpieczeń niestandardowych
 Aby włączyć token zabezpieczający niestandardowych w programie WCF, Utwórz reprezentację obiektu w tokenie zabezpieczającym niestandardowych. Przykład powoduje to reprezentacja `CreditCardToken` klasy. Reprezentacja obiektu odpowiada do przechowywania wszystkich informacji o tokenie zabezpieczeń i podać listę kluczy zabezpieczeń zawartych w tokenie zabezpieczającym. W tym przypadku token zabezpieczający karty kredytowej nie zawiera żadnych klucz zabezpieczeń.

 W następnej sekcji opisano, co musi być wykonane, aby umożliwić niestandardowy token mają być przekazywane przewodowo i używane przez punkt końcowy usługi WCF.

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
            throw new ArgumentNullException("cardInfo");

        if (id == null)
            throw new ArgumentNullException("id");

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Pobieranie tokenu do i z komunikatu niestandardowej karty kredytowej
 Serializatory tokenu zabezpieczeń programu WCF jest odpowiedzialny za tworzenie reprezentację obiektu w tokeny zabezpieczające z pliku XML w komunikacie i tworzenie tokenów zabezpieczających w formacie XML. Są one również odpowiedzialny za inne funkcje, takie jak odczytywanie i zapisywanie klucza identyfikatory wskazujący tokenów zabezpieczających, ale w tym przykładzie użyto tylko funkcji skojarzone z tokenem zabezpieczeń. Aby włączyć niestandardową tokenu należy zaimplementować własny Serializator tokenów zabezpieczeń. W tym przykładzie użyto `CreditCardSecurityTokenSerializer` klasy, w tym celu.

 W usłudze niestandardowy serializator odczytuje w formacie XML niestandardowy token i tworzy reprezentację niestandardowego obiektu tokenu z niego.

 Na komputerze klienckim `CreditCardSecurityTokenSerializer` klasy zapisuje informacji zawartych w reprezentacji obiektu tokenu zabezpieczeń do edytora XML.

```csharp
public class CreditCardSecurityTokenSerializer : WSSecurityTokenSerializer
{
    public CreditCardSecurityTokenSerializer(SecurityTokenVersion version) : base() { }

    protected override bool CanReadTokenCore(XmlReader reader)
    {
        XmlDictionaryReader localReader = XmlDictionaryReader.CreateDictionaryReader(reader);

        if (reader == null) throw new ArgumentNullException("reader");

        if (reader.IsStartElement(Constants.CreditCardTokenName, Constants.CreditCardTokenNamespace))
            return true;

        return base.CanReadTokenCore(reader);
    }

    protected override SecurityToken ReadTokenCore(XmlReader reader, SecurityTokenResolver tokenResolver)
    {
        if (reader == null) throw new ArgumentNullException("reader");

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

            CreditCardInfo cardInfo = new CreditCardInfo(creditCardNumber, creditCardIssuer, expirationTime);

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

        else
            return base.CanWriteTokenCore(token);
    }

    protected override void WriteTokenCore(XmlWriter writer, SecurityToken token)
    {
        if (writer == null) { throw new ArgumentNullException("writer"); }
        if (token == null) { throw new ArgumentNullException("token"); }

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Sposób tworzenia dostawcy tokenów i tokenów klasy wystawcy uwierzytelnienia
 Poświadczenia klienta i usługi są odpowiedzialne za świadczenie wystąpienia Menedżer tokenów zabezpieczeń. Wystąpienia Menedżer tokenów zabezpieczeń jest używany do dostawcy tokenów, wystawców uwierzytelnienia tokenu i serializatorów tokenu.

 Dostawcy tokenu, który tworzy reprezentację obiektu tokenu, na podstawie informacji zawartych w poświadczeniach klienta lub usługę. Reprezentacja obiektu tokenu są następnie zapisywane do wiadomości za pomocą Serializator tokenów (opisanych w poprzedniej sekcji).

 Wystawca uwierzytelnienia tokenów sprawdza poprawność tokenów, które zostaną odebrane w wiadomości. Przychodzący reprezentację obiektu tokenu jest tworzony przez Serializator tokenów. Taka reprezentacja obiektu jest następnie przekazywany do wystawcy uwierzytelniania tokenu weryfikacji. Po pomyślnym zweryfikowaniu tokenu, wystawca uwierzytelnienia tokenów zwraca kolekcję `IAuthorizationPolicy` obiektami, które reprezentują informacje zawarte w tokenie. Te informacje jest później używane podczas przetwarzania komunikatu do wykonywania decyzji dotyczących autoryzacji i dostarczanie oświadczeń dla aplikacji. W tym przykładzie używa wystawcy uwierzytelniania tokenu karty kredytowej `CreditCardTokenAuthorizationPolicy` do tego celu.

 Serializator tokenów jest odpowiedzialny za pobieranie reprezentacja obiektu tokenu do i z sieci. Zostało to omówione w poprzedniej sekcji.

 W tym przykładzie używamy dostawcę tokenów tylko na kliencie i wystawcy uwierzytelnienia tokenu tylko w usłudze, ponieważ chcemy, aby przesyłać token karty kredytowej, tylko w kierunku usługi klienta.

 Funkcje na komputerze klienckim znajdują się w `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` i `CreditCardTokenProvider` klasy.

 W usłudze funkcji znajduje się w `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` i `CreditCardTokenAuthorizationPolicy` klasy.

```csharp
    public class CreditCardClientCredentials : ClientCredentials
    {
        CreditCardInfo creditCardInfo;

        public CreditCardClientCredentials(CreditCardInfo creditCardInfo)
            : base()
        {
            if (creditCardInfo == null)
                throw new ArgumentNullException("creditCardInfo");

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
            // handle this token for Custom
            if (tokenRequirement.TokenType == Constants.CreditCardTokenType)
                return new CreditCardTokenProvider(this.creditCardClientCredentials.CreditCardInfo);
            // return server cert
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
            {
                throw new ArgumentNullException("creditCardInfo");
            }
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
                throw new ArgumentNullException("creditCardFile");

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
                throw new SecurityTokenValidationException("The credit card has expired");
            if (!IsCardNumberAndExpirationValid(creditCardToken.CardInfo))
                throw new SecurityTokenValidationException("Unknown or invalid credit card");

            // the credit card token has only 1 claim - the card number. The issuer for the claim is the
            // credit card issuer

            DefaultClaimSet cardIssuerClaimSet = new DefaultClaimSet(new Claim(ClaimTypes.Name, creditCardToken.CardInfo.CardIssuer, Rights.PossessProperty));
            DefaultClaimSet cardClaimSet = new DefaultClaimSet(cardIssuerClaimSet, new Claim(Constants.CreditCardNumberClaim, creditCardToken.CardInfo.CardNumber, Rights.PossessProperty));
            List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
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
                using (StreamReader myStreamReader = new StreamReader(this.creditCardsFile))
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
                throw new ArgumentNullException("issuedClaims");
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

## <a name="displaying-the-callers-information"></a>Wyświetlanie informacji o wywołującym
 Aby wyświetlić informacje o wywołującym, użyj `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym przykładowym kodzie. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczenia skojarzone z bieżącego obiektu wywołującego. Oświadczenia są dostarczane przez `CreditCardToken` klasy w jego `AuthorizationPolicies` kolekcji.

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

 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.

## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy
 Plik wsadowy Setup.bat jest dołączone do tego przykładu umożliwia skonfigurowanie serwera za pomocą odpowiednich certyfikatów do uruchamiania aplikacji hostowanych przez usługi IIS wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, działają na różnych komputerach lub działać w przypadku innych obsługiwanych.

 Poniżej zawiera krótkie omówienie różne sekcje w plikach wsadowych, dzięki czemu można modyfikować do uruchomienia w odpowiedniej konfiguracji.

-   Tworzenie certyfikatu serwera:

     Następujące wiersze z `Setup.bat` plik wsadowy utworzenie certyfikatu serwera, który ma być używany. `%SERVER_NAME%` Zmienna Określa nazwę serwera. Zmieniać tej zmiennej do określenia nazwy serwera. Domyślnie ten plik wsadowy jest localhost. Jeśli zmienisz `%SERVER_NAME%` zmiennych, musisz przejść przez pliki Client.cs i Service.cs i Zamień wszystkie wystąpienia elementu localhost nazwę serwera, którego używasz w skrypt Setup.bat jest.

     Certyfikat jest przechowywany w magazynie użytkownika (osobistych) w obszarze `LocalMachine` lokalizacji magazynu. Certyfikat jest przechowywany w magazynie usług hostowanych przez usługi IIS. Samodzielnie hostowany usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu klienta w lokalizacji magazynu CurrentUser, zastępując ciąg LocalMachine CurrentUser.

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

-   Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:

     Przechowywać następujące wiersze w Setup.bat jest kopia pliku wsadowego certyfikatu serwera do klienta zaufanych osób. Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta. Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony firmy Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

-   Aby włączyć dostęp do klucza prywatnego certyfikatu z usług hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dla klucza prywatnego. Jest to realizowane przez ostatnie kroki skrypt Setup.bat jest.

    ```
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
>  Plik wsadowy Setup.bat jest przeznaczony do uruchamiania z programu Visual Studio 2012 wiersz polecenia. Ustaw w Visual Studio 2012 Command Prompt punkty do katalogu, który zawiera pliki wykonywalne wymagane przez skrypt Setup.bat jest zmiennej środowiskowej PATH.

#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład

1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze

1.  Otwórz okno wiersza polecenia 2012 w usłudze Visual Studio z uprawnieniami administratora i uruchom Setup.bat jest z poziomu folderu instalacji przykładowej. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.

> [!NOTE]
>  Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu pracy z przykładem. Inne przykłady zabezpieczeń za pomocą tych samych certyfikatów.  
  
1.  Uruchom Client.exe z katalogu client\bin. Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.  
  
2.  Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computer"></a>Do uruchomienia przykładu na komputer  
  
1.  Utwórz katalog na komputerze usługi, aby pliki binarne usługi.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Pamiętaj skopiować CreditCardFile.txt; w przeciwnym razie authenticator karta kredytowa nie można zweryfikować informacji o karcie kredytowej wysłanych z klienta. Także skopiować pliki Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera o nazwie podmiotu, który zawiera w pełni kwalifikowana nazwa domeny komputera. Możesz je utworzyć za pomocą Setup.bat, jeśli zmienisz `%SERVER_NAME%` zmiennej do w pełni kwalifikowaną nazwę komputera, na którym jest hostowana usługa. Należy pamiętać, że plik Setup.bat jest należy uruchomić polecenie w wierszu polecenia programu Visual Studio, otwartych z uprawnieniami administratora.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople na komputerze klienckim. Należy to zrobić tylko wtedy, gdy certyfikat serwera nie jest wystawiony przez zaufanego wystawcy.  
  
5.  W pliku EchoServiceHost.cs należy zmienić wartość Nazwa podmiotu certyfikatu, aby określić nazwę komputera w pełni kwalifikowaną, zamiast nazwy localhost.  
  
6.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerze klienckim.  
  
7.  W pliku Client.cs Zmień wartość adresu punktu końcowego, aby dopasować nowy adres usługi.  
  
8.  W pliku Client.cs należy zmienić nazwę podmiotu certyfikatu X.509 service, aby pasować do nazwy komputera w pełni kwalifikowana hosta zdalnego zamiast nazwy localhost.  
  
9. Na komputerze klienckim, aby uruchomić Client.exe z okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić zasoby po próbki  
  
1.  Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.  
  
## <a name="see-also"></a>Zobacz też
