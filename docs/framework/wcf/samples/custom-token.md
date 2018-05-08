---
title: Token niestandardowy
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: 5850f97d6d3a66aacf82ab1cb2338240a75a00fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="custom-token"></a>Token niestandardowy
Ten przykład przedstawia sposób dodawania niestandardowych implementacji token do aplikacji Windows Communication Foundation (WCF). W przykładzie użyto `CreditCardToken` do bezpieczne przekazywanie informacji o kartach kredytowych klienta do usługi. Token jest przekazywany w nagłówku wiadomości WS-Security jest podpisany i szyfrowana przy użyciu elementu powiązania zabezpieczeń symetrycznego wraz z treści wiadomości i innych nagłówków komunikatów. Jest to przydatne w sytuacjach, gdy wbudowanych tokenów nie są wystarczające. W tym przykładzie pokazano, jak zapewnić tokenu zabezpieczeń niestandardowej z usługą zamiast przy użyciu jednej z wbudowanych tokenów. Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Krótko mówiąc, w tym przykładzie przedstawiono poniżej:  
  
-   Jak klient może przekazać tokenu zabezpieczającego niestandardowych do usługi.  
  
-   Jak usługa może wykorzystywać i zweryfikować tokenu zabezpieczającego niestandardowych.  
  
-   Jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kodu usługi można uzyskać informacje na temat tokeny zabezpieczające odebrane wraz z tokenem niestandardowy zabezpieczeń.  
  
-   Jak certyfikat X.509 służy do ochrony klucz symetryczny stosowany do szyfrowania wiadomości i podpis.  
  
## <a name="client-authentication-using-a-custom-security-token"></a>Uwierzytelnianie klienta przy użyciu tokenu zabezpieczającego niestandardowych  
 Usługa udostępnia pojedynczy punkt końcowy, który jest tworzony programowo przy użyciu `BindingHelper` i `EchoServiceHost` klasy. Punkt końcowy składa się z adresu, powiązania i kontrakt. Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`. W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikat X.509 usługi ochrony klucza symetrycznego podczas transmisji oraz przekazywanie niestandardowej `CreditCardToken` w nagłówku wiadomości WS-Security jako tokenu zabezpieczającego podpisane i zaszyfrowane. Zachowanie Określa poświadczenia usługi, które mają być używane uwierzytelnianie klienta, a także informacje o certyfikat X.509 usługi.  
  
```  
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
  
 Użycie karty kredytowej token w komunikacie, próbki używa usług niestandardowych poświadczeń do tej funkcji. Klasa poświadczenia usługi znajduje się w `CreditCardServiceCredentials` klasy i zostanie dodany do kolekcji zachowań usługi hosta w `EchoServiceHost.InitializeRuntime` metody.  
  
```  
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
  
 Punkt końcowy klienta jest skonfigurowany w sposób podobny jako punktu końcowego usługi. Klient używa takie same `BindingHelper` klasy w celu utworzenia powiązania. Pozostała konfiguracja znajduje się w `Client` klasy. Klient ustawia również informacje zawarte w `CreditCardToken` i informacji dotyczących certyfikatu X.509 usługi w kodzie instalacji przez dodanie `CreditCardClientCredentials` wystąpienia o odpowiednie dane do kolekcji zachowań klienta punktu końcowego. W przykładzie użyto certyfikatu X.509 z nazwą podmiotu ustawioną `CN=localhost` jako certyfikat usługi.  
  
```  
Binding creditCardBinding = BindingHelper.CreateCreditCardBinding();  
EndpointAddress serviceAddress = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
  
// Create a client with given client endpoint configuration  
channelFactory =   
new ChannelFactory<IEchoService>(creditCardBinding, serviceAddress);  
  
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
 Aby włączyć tokenu zabezpieczającego niestandardowych w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Utwórz obiekt reprezentację tokenu zabezpieczającego niestandardowych. Próbka ma taka reprezentacja w `CreditCardToken` klasy. Reprezentacja obiektu odpowiada do przechowywania wszystkich informacji o tokenie zabezpieczeń oraz zamieszczono listę kluczy zabezpieczeń zawartych w tokenie zabezpieczającym. W takim przypadku tokenu zabezpieczającego karty kredytowej nie zawiera żadnych klucz zabezpieczeń.  
  
 W następnej sekcji opisano, co można zrobić, aby włączyć niestandardowy token przesyłane przez sieć i używane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktu końcowego.  
  
```  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a>Pobieranie tokenu z komunikatu i niestandardowe karty kredytowej  
 Serializatorów tokenu zabezpieczeń w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] są odpowiedzialne za tworzenie obiektu reprezentację tokeny zabezpieczające z pliku XML w komunikacie i tworzenie formularza XML tokenów zabezpieczających. Są one również odpowiedzialne za inne funkcje, takie jak odczytywanie i zapisywanie klucza identyfikatory wskazujący tokeny zabezpieczające, ale w tym przykładzie użyto tylko funkcji związanych z tokenu zabezpieczeń. Aby włączyć niestandardowy token należy zaimplementować własny Serializator tokenu zabezpieczającego. W przykładzie użyto `CreditCardSecurityTokenSerializer` klasy w tym celu.  
  
 W usłudze serializatora niestandardowego odczytuje formularz XML tokenu niestandardowego i tworzy reprezentację niestandardowego obiektu tokenu z niego.  
  
 Na komputerze klienckim `CreditCardSecurityTokenSerializer` klasy zapisuje informacje zawarte w reprezentacji obiektu tokenu zabezpieczeń do edytora XML.  
  
```  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a>Sposób tworzenia dostawcy tokenu i klasy wystawcy uwierzytelnienia tokenu  
 Klient i usługa poświadczenia spoczywa odpowiedzialność za zapewnienie wystąpienia Menedżer tokenów zabezpieczeń. Wystąpienia Menedżer tokenów zabezpieczeń jest używany do pobierania tokenu dostawców, wystawcy uwierzytelnienia tokenu i serializatorów tokenu.  
  
 Dostawca tokenu tworzy reprezentację obiektu tokenu na podstawie informacji zawartych w poświadczeniach klienta lub usługi. Reprezentacja obiektu tokenu następnie jest zapisywany komunikat przy użyciu serializatora tokenu (opisanych w poprzedniej sekcji).  
  
 Wystawcy uwierzytelnienia tokenu weryfikuje tokeny pojawiające się w komunikacie. Przychodzącego reprezentację obiektu tokenu jest tworzony przez Serializator tokenów. Taka reprezentacja obiektu są następnie przekazywane wystawcy uwierzytelnienia tokenu dla weryfikacji. Po pomyślnym uwierzytelnieniu token wystawcy uwierzytelnienia tokenu zwraca kolekcję `IAuthorizationPolicy` obiektów, które reprezentują informacji zawartych w tokenie. Te informacje jest używana później podczas przetwarzania komunikatu do wykonywania decyzji dotyczących autoryzacji i dostarczania oświadczeń dla aplikacji. W tym przykładzie używa wystawcy uwierzytelnienia tokenu karty kredytowej `CreditCardTokenAuthorizationPolicy` w tym celu.  
  
 Serializator tokenów jest odpowiedzialny za pobieranie reprezentację obiektu tokenu do i z sieci. Jest to opisanych w poprzedniej sekcji.  
  
 W tym przykładzie używamy dostawcę tokenów tylko na kliencie i wystawcy uwierzytelnienia tokenu tylko w ramach usługi, ponieważ chcemy, aby przesyłać token karty kredytowej tylko w kierunku usługi klienta.  
  
 Funkcje klienta znajduje się w `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` i `CreditCardTokenProvider` klasy.  
  
 W usłudze funkcji znajduje się w `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` i `CreditCardTokenAuthorizationPolicy` klasy.  
  
```  
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
  
## <a name="displaying-the-callers-information"></a>Wyświetlanie informacji wywołań  
 Aby wyświetlić informacje o wywołującym, użyj `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie próbki. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczeń skojarzone z bieżącym obiektem wywołującym. Oświadczenia są dostarczane przez `CreditCardToken` klasy w jego `AuthorizationPolicies` kolekcji.  
  
```  
bool TryGetStringClaimValue(ClaimSet claimSet, string claimType, out string claimValue)  
{  
    claimValue = null;  
    IEnumerable<Claim> matchingClaims = claimSet.FindClaims(claimType,  
        Rights.PossessProperty);  
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
                 return String.Format(  
                   "Credit card '{0}' issued by '{1}'",   
                   creditCardNumber, issuer);  
        }  
    }  
    return "Credit card is not known";  
}  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
## <a name="setup-batch-file"></a>Instalacyjny plik wsadowy  
 Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów na uruchamianie aplikacji hostowanych przez usługi IIS wymaga zabezpieczeń na podstawie certyfikatu serwera. Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.  
  
 Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.  
  
-   Tworzenie certyfikatu serwera:  
  
     Następujące wiersze z `Setup.bat` plik wsadowy utworzenie certyfikatu serwera do użycia. `%SERVER_NAME%` Zmiennej określa nazwę serwera. Zmień tę wartość, aby określić nazwę serwera. Domyślnie ten plik wsadowy jest localhost. Jeśli zmienisz `%SERVER_NAME%` zmiennej, należy przejść przez pliki Client.cs i Service.cs i Zastąp wszystkie wystąpienia zmiennej localhost z nazwą serwera używanego w pliku Setup.bat skryptu.  
  
     Certyfikat jest przechowywany w magazynie My (osobistych) w obszarze `LocalMachine` lokalizacji magazynu. Certyfikat jest przechowywany w magazynie LocalMachine usług hostowanych przez usługi IIS. Hostowanie Samoobsługowe usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu klienta w lokalizacji magazynu CurrentUser, zastępując ciąg LocalMachine CurrentUser.  
  
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
  
     Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu. Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta. Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   Aby włączyć dostęp do klucza prywatnego certyfikatu usługi hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dostępu do klucza prywatnego. Jest to osiągane przez ostatnich kroków w skrypcie pliku Setup.bat.  
  
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
>  Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia. Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.  
  
#### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] okno wiersza polecenia z uprawnieniami administratora i wykonywania pliku Setup.bat z folderu instalacyjnego próbki. Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.  
  
> [!NOTE]
>  Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu próbki. Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.  
  
1.  Uruchom Client.exe z katalogu client\bin. Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.  
  
2.  Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-run-the-sample-across-computer"></a>Aby uruchomić przykład na komputerze  
  
1.  Utwórz katalog na komputerze usługi dla usługi danych binarnych.  
  
2.  Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi. Pamiętaj skopiować CreditCardFile.txt; w przeciwnym razie wystawcy uwierzytelnienia karty kredytowej nie można sprawdzić poprawności informacji o karcie kredytowej wysłanych z klienta. Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.  
  
3.  Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera. Można go utworzyć przy użyciu pliku Setup.bat, jeśli zmienisz `%SERVER_NAME%` zmiennej w pełni kwalifikowaną nazwę komputera, na którym jest hostowana usługa. Należy pamiętać, że plik pliku Setup.bat musi zostać uruchomiony w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora.  
  
4.  Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople na kliencie. Należy to zrobić tylko, jeśli certyfikat serwera nie jest wystawiany przez zaufanych wystawców.  
  
5.  W pliku EchoServiceHost.cs Zmień wartość nazwy podmiotu certyfikatu do określenia nazwy komputera w pełni kwalifikowana, zamiast localhost.  
  
6.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.  
  
7.  W pliku Client.cs Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.  
  
8.  W pliku Client.cs Zmień nazwę podmiotu certyfikatu X.509 usługi, aby dopasować komputera w pełni kwalifikowaną nazwę hosta zdalnego zamiast localhost.  
  
9. Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia.  
  
10. Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
#### <a name="to-clean-up-after-the-sample"></a>Aby wyczyścić po próbki  
  
1.  Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.  
  
## <a name="see-also"></a>Zobacz też
