---
title: Token niestandardowy
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: c7219b94861cd23f27b331d1d3e5509654263430
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="custom-token"></a><span data-ttu-id="5d4b1-102">Token niestandardowy</span><span class="sxs-lookup"><span data-stu-id="5d4b1-102">Custom Token</span></span>
<span data-ttu-id="5d4b1-103">Ten przykład przedstawia sposób dodawania niestandardowych implementacji token do aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5d4b1-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5d4b1-104">W przykładzie użyto `CreditCardToken` do bezpieczne przekazywanie informacji o kartach kredytowych klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="5d4b1-105">Token jest przekazywany w nagłówku wiadomości WS-Security jest podpisany i szyfrowana przy użyciu elementu powiązania zabezpieczeń symetrycznego wraz z treści wiadomości i innych nagłówków komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="5d4b1-106">Jest to przydatne w sytuacjach, gdy wbudowanych tokenów nie są wystarczające.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="5d4b1-107">W tym przykładzie pokazano, jak zapewnić tokenu zabezpieczeń niestandardowej z usługą zamiast przy użyciu jednej z wbudowanych tokenów.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="5d4b1-108">Usługa implementuje kontrakt definiuje wzorzec komunikacji żądanie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d4b1-109">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5d4b1-110">Krótko mówiąc, w tym przykładzie przedstawiono poniżej:</span><span class="sxs-lookup"><span data-stu-id="5d4b1-110">To summarize, this sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="5d4b1-111">Jak klient może przekazać tokenu zabezpieczającego niestandardowych do usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-111">How a client can pass a custom security token to a service.</span></span>  
  
-   <span data-ttu-id="5d4b1-112">Jak usługa może wykorzystywać i zweryfikować tokenu zabezpieczającego niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-112">How the service can consume and validate a custom security token.</span></span>  
  
-   <span data-ttu-id="5d4b1-113">Jak kodu usługi WCF można uzyskać informacje na temat tokeny zabezpieczające odebrane wraz z tokenem niestandardowy zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>  
  
-   <span data-ttu-id="5d4b1-114">Jak certyfikat X.509 służy do ochrony klucz symetryczny stosowany do szyfrowania wiadomości i podpis.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>  
  
## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="5d4b1-115">Uwierzytelnianie klienta przy użyciu tokenu zabezpieczającego niestandardowych</span><span class="sxs-lookup"><span data-stu-id="5d4b1-115">Client Authentication Using a Custom Security Token</span></span>  
 <span data-ttu-id="5d4b1-116">Usługa udostępnia pojedynczy punkt końcowy, który jest tworzony programowo przy użyciu `BindingHelper` i `EchoServiceHost` klasy.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="5d4b1-117">Punkt końcowy składa się z adresu, powiązania i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="5d4b1-118">Powiązanie jest skonfigurowane z niestandardowego powiązania za pomocą `SymmetricSecurityBindingElement` i `HttpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="5d4b1-119">W tym przykładzie ustawia `SymmetricSecurityBindingElement` do użycia certyfikat X.509 usługi ochrony klucza symetrycznego podczas transmisji oraz przekazywanie niestandardowej `CreditCardToken` w nagłówku wiadomości WS-Security jako tokenu zabezpieczającego podpisane i zaszyfrowane.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="5d4b1-120">Zachowanie Określa poświadczenia usługi, które mają być używane uwierzytelnianie klienta, a także informacje o certyfikat X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>  
  
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
  
 <span data-ttu-id="5d4b1-121">Użycie karty kredytowej token w komunikacie, próbki używa usług niestandardowych poświadczeń do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="5d4b1-122">Klasa poświadczenia usługi znajduje się w `CreditCardServiceCredentials` klasy i zostanie dodany do kolekcji zachowań usługi hosta w `EchoServiceHost.InitializeRuntime` metody.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>  
  
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
  
 <span data-ttu-id="5d4b1-123">Punkt końcowy klienta jest skonfigurowany w sposób podobny jako punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="5d4b1-124">Klient używa takie same `BindingHelper` klasy w celu utworzenia powiązania.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="5d4b1-125">Pozostała konfiguracja znajduje się w `Client` klasy.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="5d4b1-126">Klient ustawia również informacje zawarte w `CreditCardToken` i informacji dotyczących certyfikatu X.509 usługi w kodzie instalacji przez dodanie `CreditCardClientCredentials` wystąpienia o odpowiednie dane do kolekcji zachowań klienta punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="5d4b1-127">W przykładzie użyto certyfikatu X.509 z nazwą podmiotu ustawioną `CN=localhost` jako certyfikat usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>  
  
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
  
## <a name="custom-security-token-implementation"></a><span data-ttu-id="5d4b1-128">Implementacja tokenu zabezpieczeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="5d4b1-128">Custom Security Token Implementation</span></span>  
 <span data-ttu-id="5d4b1-129">Aby włączyć tokenu zabezpieczającego niestandardowych w programie WCF, Utwórz obiekt reprezentację tokenu zabezpieczającego niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="5d4b1-130">Próbka ma taka reprezentacja w `CreditCardToken` klasy.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="5d4b1-131">Reprezentacja obiektu odpowiada do przechowywania wszystkich informacji o tokenie zabezpieczeń oraz zamieszczono listę kluczy zabezpieczeń zawartych w tokenie zabezpieczającym.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="5d4b1-132">W takim przypadku tokenu zabezpieczającego karty kredytowej nie zawiera żadnych klucz zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-132">In this case, the credit card security token does not contain any security key.</span></span>  
  
 <span data-ttu-id="5d4b1-133">W następnej sekcji opisano, co należy wykonać, aby włączyć niestandardowy token przesyłane przez sieć i używane przez punkt końcowy usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>  
  
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
  
## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="5d4b1-134">Pobieranie tokenu z komunikatu i niestandardowe karty kredytowej</span><span class="sxs-lookup"><span data-stu-id="5d4b1-134">Getting the Custom Credit Card Token to and from the Message</span></span>  
 <span data-ttu-id="5d4b1-135">Serializatorów tokenu zabezpieczeń w programie WCF są odpowiedzialne za tworzenie obiektu reprezentację tokeny zabezpieczające z pliku XML w komunikacie i tworzenie formularza XML tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="5d4b1-136">Są one również odpowiedzialne za inne funkcje, takie jak odczytywanie i zapisywanie klucza identyfikatory wskazujący tokeny zabezpieczające, ale w tym przykładzie użyto tylko funkcji związanych z tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="5d4b1-137">Aby włączyć niestandardowy token należy zaimplementować własny Serializator tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="5d4b1-138">W przykładzie użyto `CreditCardSecurityTokenSerializer` klasy w tym celu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>  
  
 <span data-ttu-id="5d4b1-139">W usłudze serializatora niestandardowego odczytuje formularz XML tokenu niestandardowego i tworzy reprezentację niestandardowego obiektu tokenu z niego.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>  
  
 <span data-ttu-id="5d4b1-140">Na komputerze klienckim `CreditCardSecurityTokenSerializer` klasy zapisuje informacje zawarte w reprezentacji obiektu tokenu zabezpieczeń do edytora XML.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>  
  
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
  
## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="5d4b1-141">Sposób tworzenia dostawcy tokenu i klasy wystawcy uwierzytelnienia tokenu</span><span class="sxs-lookup"><span data-stu-id="5d4b1-141">How Token Provider and Token Authenticator Classes are Created</span></span>  
 <span data-ttu-id="5d4b1-142">Klient i usługa poświadczenia spoczywa odpowiedzialność za zapewnienie wystąpienia Menedżer tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="5d4b1-143">Wystąpienia Menedżer tokenów zabezpieczeń jest używany do pobierania tokenu dostawców, wystawcy uwierzytelnienia tokenu i serializatorów tokenu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>  
  
 <span data-ttu-id="5d4b1-144">Dostawca tokenu tworzy reprezentację obiektu tokenu na podstawie informacji zawartych w poświadczeniach klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="5d4b1-145">Reprezentacja obiektu tokenu następnie jest zapisywany komunikat przy użyciu serializatora tokenu (opisanych w poprzedniej sekcji).</span><span class="sxs-lookup"><span data-stu-id="5d4b1-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>  
  
 <span data-ttu-id="5d4b1-146">Wystawcy uwierzytelnienia tokenu weryfikuje tokeny pojawiające się w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="5d4b1-147">Przychodzącego reprezentację obiektu tokenu jest tworzony przez Serializator tokenów.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="5d4b1-148">Taka reprezentacja obiektu są następnie przekazywane wystawcy uwierzytelnienia tokenu dla weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="5d4b1-149">Po pomyślnym uwierzytelnieniu token wystawcy uwierzytelnienia tokenu zwraca kolekcję `IAuthorizationPolicy` obiektów, które reprezentują informacji zawartych w tokenie.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="5d4b1-150">Te informacje jest używana później podczas przetwarzania komunikatu do wykonywania decyzji dotyczących autoryzacji i dostarczania oświadczeń dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="5d4b1-151">W tym przykładzie używa wystawcy uwierzytelnienia tokenu karty kredytowej `CreditCardTokenAuthorizationPolicy` w tym celu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>  
  
 <span data-ttu-id="5d4b1-152">Serializator tokenów jest odpowiedzialny za pobieranie reprezentację obiektu tokenu do i z sieci.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="5d4b1-153">Jest to opisanych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-153">This is discussed in the previous section.</span></span>  
  
 <span data-ttu-id="5d4b1-154">W tym przykładzie używamy dostawcę tokenów tylko na kliencie i wystawcy uwierzytelnienia tokenu tylko w ramach usługi, ponieważ chcemy, aby przesyłać token karty kredytowej tylko w kierunku usługi klienta.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>  
  
 <span data-ttu-id="5d4b1-155">Funkcje klienta znajduje się w `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` i `CreditCardTokenProvider` klasy.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-155">The functionality on the client is located in the `CreditCardClientCrendentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>  
  
 <span data-ttu-id="5d4b1-156">W usłudze funkcji znajduje się w `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` i `CreditCardTokenAuthorizationPolicy` klasy.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>  
  
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
  
## <a name="displaying-the-callers-information"></a><span data-ttu-id="5d4b1-157">Wyświetlanie informacji wywołań</span><span class="sxs-lookup"><span data-stu-id="5d4b1-157">Displaying the Callers' Information</span></span>  
 <span data-ttu-id="5d4b1-158">Aby wyświetlić informacje o wywołującym, użyj `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="5d4b1-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera autoryzacji oświadczeń skojarzone z bieżącym obiektem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="5d4b1-160">Oświadczenia są dostarczane przez `CreditCardToken` klasy w jego `AuthorizationPolicies` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>  
  
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
  
 <span data-ttu-id="5d4b1-161">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5d4b1-162">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-162">Press ENTER in the client window to shut down the client.</span></span>  
  
## <a name="setup-batch-file"></a><span data-ttu-id="5d4b1-163">Instalacyjny plik wsadowy</span><span class="sxs-lookup"><span data-stu-id="5d4b1-163">Setup Batch File</span></span>  
 <span data-ttu-id="5d4b1-164">Plik wsadowy pliku Setup.bat uwzględnionych w tym przykładzie pozwala na skonfigurowanie serwera z odpowiednich certyfikatów na uruchamianie aplikacji hostowanych przez usługi IIS wymaga zabezpieczeń na podstawie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="5d4b1-165">Ten plik wsadowy muszą zostać zmodyfikowane, aby pracować na komputerach lub do pracy w przypadku z systemem innym niż obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="5d4b1-166">Poniżej zawiera krótki przegląd różnych sekcji pliki wsadowe tak, aby można modyfikować w prawidłowej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
-   <span data-ttu-id="5d4b1-167">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="5d4b1-167">Creating the server certificate:</span></span>  
  
     <span data-ttu-id="5d4b1-168">Następujące wiersze z `Setup.bat` plik wsadowy utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="5d4b1-169">`%SERVER_NAME%` Zmiennej określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="5d4b1-170">Zmień tę wartość, aby określić nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="5d4b1-171">Domyślnie ten plik wsadowy jest localhost.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="5d4b1-172">Jeśli zmienisz `%SERVER_NAME%` zmiennej, należy przejść przez pliki Client.cs i Service.cs i Zastąp wszystkie wystąpienia zmiennej localhost z nazwą serwera używanego w pliku Setup.bat skryptu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>  
  
     <span data-ttu-id="5d4b1-173">Certyfikat jest przechowywany w magazynie My (osobistych) w obszarze `LocalMachine` lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="5d4b1-174">Certyfikat jest przechowywany w magazynie LocalMachine usług hostowanych przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="5d4b1-175">Hostowanie Samoobsługowe usług należy zmodyfikować plik wsadowy do przechowywania certyfikatu klienta w lokalizacji magazynu CurrentUser, zastępując ciąg LocalMachine CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
-   <span data-ttu-id="5d4b1-176">Instalowanie certyfikatu serwera do magazynu zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="5d4b1-176">Installing the server certificate into client's trusted certificate store:</span></span>  
  
     <span data-ttu-id="5d4b1-177">Następujące wiersze w pliku Setup.bat kopii pliku wsadowego certyfikatu serwera do klienta zaufanych osób magazynu.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="5d4b1-178">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="5d4b1-179">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład Microsoft wystawiony certyfikat — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    echo ************  
    echo copying server cert to client's TrustedPeople store  
    echo ************  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
-   <span data-ttu-id="5d4b1-180">Aby włączyć dostęp do klucza prywatnego certyfikatu usługi hostowanych przez usługi IIS, konto użytkownika, na którym uruchomiono proces hostowanych przez usługi IIS musi otrzymać odpowiednie uprawnienia dostępu do klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="5d4b1-181">Jest to osiągane przez ostatnich kroków w skrypcie pliku Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-181">This is accomplished by last steps in the Setup.bat script.</span></span>  
  
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
>  <span data-ttu-id="5d4b1-182">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-182">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="5d4b1-183">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-183">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="5d4b1-184">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="5d4b1-184">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="5d4b1-185">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5d4b1-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="5d4b1-186">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5d4b1-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5d4b1-187">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="5d4b1-187">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="5d4b1-188">Otwórz [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] okno wiersza polecenia z uprawnieniami administratora i wykonywania pliku Setup.bat z folderu instalacyjnego próbki.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-188">Open a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="5d4b1-189">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d4b1-190">Pamiętaj usunąć certyfikaty, uruchamiając Cleanup.bat po zakończeniu próbki.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="5d4b1-191">Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-191">Other security samples use the same certificates.</span></span>  
  
1.  <span data-ttu-id="5d4b1-192">Uruchom Client.exe z katalogu client\bin.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="5d4b1-193">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-193">Client activity is displayed on the client console application.</span></span>  
  
2.  <span data-ttu-id="5d4b1-194">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5d4b1-194">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="5d4b1-195">Aby uruchomić przykład na komputerze</span><span class="sxs-lookup"><span data-stu-id="5d4b1-195">To run the sample across computer</span></span>  
  
1.  <span data-ttu-id="5d4b1-196">Utwórz katalog na komputerze usługi dla usługi danych binarnych.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2.  <span data-ttu-id="5d4b1-197">Skopiuj pliki programu usługi do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="5d4b1-198">Pamiętaj skopiować CreditCardFile.txt; w przeciwnym razie wystawcy uwierzytelnienia karty kredytowej nie można sprawdzić poprawności informacji o karcie kredytowej wysłanych z klienta.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="5d4b1-199">Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3.  <span data-ttu-id="5d4b1-200">Musi mieć certyfikat serwera z nazwą podmiotu, który zawiera w pełni kwalifikowaną nazwą domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="5d4b1-201">Można go utworzyć przy użyciu pliku Setup.bat, jeśli zmienisz `%SERVER_NAME%` zmiennej w pełni kwalifikowaną nazwę komputera, na którym jest hostowana usługa.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="5d4b1-202">Należy pamiętać, że plik pliku Setup.bat musi zostać uruchomiony w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-202">Note that the Setup.bat file must be run in a Visual Studio command prompt opened with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="5d4b1-203">Skopiuj certyfikat serwera w magazynie CurrentUser TrustedPeople na kliencie.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="5d4b1-204">Należy to zrobić tylko, jeśli certyfikat serwera nie jest wystawiany przez zaufanych wystawców.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5.  <span data-ttu-id="5d4b1-205">W pliku EchoServiceHost.cs Zmień wartość nazwy podmiotu certyfikatu do określenia nazwy komputera w pełni kwalifikowana, zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6.  <span data-ttu-id="5d4b1-206">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7.  <span data-ttu-id="5d4b1-207">W pliku Client.cs Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8.  <span data-ttu-id="5d4b1-208">W pliku Client.cs Zmień nazwę podmiotu certyfikatu X.509 usługi, aby dopasować komputera w pełni kwalifikowaną nazwę hosta zdalnego zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="5d4b1-209">Na komputerze klienckim uruchom Client.exe z poziomu okna wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="5d4b1-210">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="5d4b1-210">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5d4b1-211">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="5d4b1-211">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="5d4b1-212">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="5d4b1-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4b1-213">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d4b1-213">See Also</span></span>
