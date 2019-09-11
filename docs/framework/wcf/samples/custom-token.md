---
title: Token niestandardowy
ms.date: 03/30/2017
ms.assetid: e7fd8b38-c370-454f-ba3e-19759019f03d
ms.openlocfilehash: c3c6cfd9d1742f7e839d7b40220792ba455d7673
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855508"
---
# <a name="custom-token"></a><span data-ttu-id="6cf93-102">Token niestandardowy</span><span class="sxs-lookup"><span data-stu-id="6cf93-102">Custom Token</span></span>

<span data-ttu-id="6cf93-103">Ten przykład pokazuje, jak dodać implementację niestandardowego tokenu do aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6cf93-103">This sample demonstrates how to add a custom token implementation into a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="6cf93-104">W przykładzie zastosowano `CreditCardToken` do bezpiecznego przekazywania informacji o kartach kredytowych klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-104">The example uses a `CreditCardToken` to securely pass information about client credit cards to the service.</span></span> <span data-ttu-id="6cf93-105">Token jest przekazywany w nagłówku komunikatu WS-Security i jest podpisywany i szyfrowany przy użyciu elementu symetrycznego powiązania zabezpieczeń wraz z treścią komunikatu i innymi nagłówkami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6cf93-105">The token is passed in the WS-Security message header and is signed and encrypted using the symmetric security binding element along with message body and other message headers.</span></span> <span data-ttu-id="6cf93-106">Jest to przydatne w przypadku, gdy wbudowane tokeny nie są wystarczające.</span><span class="sxs-lookup"><span data-stu-id="6cf93-106">This is useful in cases where the built-in tokens are not sufficient.</span></span> <span data-ttu-id="6cf93-107">Ten przykład ilustruje sposób dostarczania niestandardowego tokenu zabezpieczającego do usługi zamiast korzystania z jednego z tokenów wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="6cf93-107">This sample demonstrates how to provide a custom security token to a service instead of using one of the built-in tokens.</span></span> <span data-ttu-id="6cf93-108">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="6cf93-108">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="6cf93-109">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="6cf93-110">Podsumowując, ten przykład ilustruje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="6cf93-110">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="6cf93-111">Sposób przekazywania przez klienta niestandardowego tokenu zabezpieczającego do usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-111">How a client can pass a custom security token to a service.</span></span>

- <span data-ttu-id="6cf93-112">Jak usługa może zużywać i sprawdzać poprawność niestandardowego tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6cf93-112">How the service can consume and validate a custom security token.</span></span>

- <span data-ttu-id="6cf93-113">Jak kod usługi WCF może uzyskać informacje o odebranych tokenach zabezpieczających, w tym o niestandardowym tokenie zabezpieczającym.</span><span class="sxs-lookup"><span data-stu-id="6cf93-113">How the WCF service code can obtain the information about received security tokens including the custom security token.</span></span>

- <span data-ttu-id="6cf93-114">Jak certyfikat X. 509 serwera jest używany do ochrony klucza symetrycznego używanego do szyfrowania i podpisywania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6cf93-114">How the server's X.509 certificate is used to protect the symmetric key used for message encryption and signature.</span></span>

## <a name="client-authentication-using-a-custom-security-token"></a><span data-ttu-id="6cf93-115">Uwierzytelnianie klienta przy użyciu niestandardowego tokenu zabezpieczającego</span><span class="sxs-lookup"><span data-stu-id="6cf93-115">Client Authentication Using a Custom Security Token</span></span>

 <span data-ttu-id="6cf93-116">Usługa ujawnia pojedynczy punkt końcowy, który jest programowo tworzony przy `BindingHelper` użyciu `EchoServiceHost` klas i.</span><span class="sxs-lookup"><span data-stu-id="6cf93-116">The service exposes a single endpoint that is programmatically created using `BindingHelper` and `EchoServiceHost` classes.</span></span> <span data-ttu-id="6cf93-117">Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-117">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="6cf93-118">Powiązanie jest skonfigurowane z powiązaniem niestandardowym `SymmetricSecurityBindingElement` przy `HttpTransportBindingElement`użyciu i.</span><span class="sxs-lookup"><span data-stu-id="6cf93-118">The binding is configured with a custom binding using `SymmetricSecurityBindingElement` and `HttpTransportBindingElement`.</span></span> <span data-ttu-id="6cf93-119">Ten przykład ustawia, `SymmetricSecurityBindingElement` aby używać certyfikatu X. 509 usługi do ochrony klucza symetrycznego podczas transmisji i do przekazywania niestandardowego `CreditCardToken` w nagłówku komunikatu WS-Security jako podpisane i zaszyfrowane tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="6cf93-119">This sample sets the `SymmetricSecurityBindingElement` to use a service's X.509 certificate to protect the symmetric key during transmission and to pass a custom `CreditCardToken` in a WS-Security message header as a signed and encrypted security token.</span></span> <span data-ttu-id="6cf93-120">Zachowanie określa poświadczenia usługi, które mają być używane do uwierzytelniania klientów, a także informacje na temat certyfikatu usługi Service X. 509.</span><span class="sxs-lookup"><span data-stu-id="6cf93-120">The behavior specifies the service credentials that are to be used for client authentication and also information about the service X.509 certificate.</span></span>

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

 <span data-ttu-id="6cf93-121">Aby korzystać z tokenu karty kredytowej w komunikacie, przykład używa niestandardowych poświadczeń usługi do zapewnienia tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-121">To consume a credit card token in the message, the sample uses custom service credentials to provide this functionality.</span></span> <span data-ttu-id="6cf93-122">Klasa poświadczeń usługi znajduje się w `CreditCardServiceCredentials` klasie i jest dodawana do kolekcji zachowań hosta usługi `EchoServiceHost.InitializeRuntime` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="6cf93-122">The service credentials class is located in the `CreditCardServiceCredentials` class and is added to the behaviors collections of the service host in the `EchoServiceHost.InitializeRuntime` method.</span></span>

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

 <span data-ttu-id="6cf93-123">Punkt końcowy klienta jest konfigurowany w podobny sposób, jak punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-123">The client endpoint is configured in a similar manner as the service endpoint.</span></span> <span data-ttu-id="6cf93-124">Klient używa tej samej `BindingHelper` klasy do utworzenia powiązania.</span><span class="sxs-lookup"><span data-stu-id="6cf93-124">The client uses the same `BindingHelper` class to create a binding.</span></span> <span data-ttu-id="6cf93-125">Pozostała część instalacji znajduje się w `Client` klasie.</span><span class="sxs-lookup"><span data-stu-id="6cf93-125">The rest of the setup is located in the `Client` class.</span></span> <span data-ttu-id="6cf93-126">Klient ustawia również informacje, które mają być zawarte w `CreditCardToken` i informacje o certyfikacie usługi X. 509 w kodzie Instalatora przez `CreditCardClientCredentials` dodanie wystąpienia z odpowiednimi danymi do kolekcji zachowań punktów końcowych klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf93-126">The client also sets information to be contained in the `CreditCardToken` and information about the service X.509 certificate in the setup code by adding a `CreditCardClientCredentials` instance with the proper data to the client endpoint behaviors collection.</span></span> <span data-ttu-id="6cf93-127">Przykład używa certyfikatu X. 509 z nazwą podmiotu ustawioną `CN=localhost` jako certyfikat usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-127">The sample uses X.509 certificate with subject name set to `CN=localhost` as the service certificate.</span></span>

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

## <a name="custom-security-token-implementation"></a><span data-ttu-id="6cf93-128">Implementacja niestandardowego tokenu zabezpieczającego</span><span class="sxs-lookup"><span data-stu-id="6cf93-128">Custom Security Token Implementation</span></span>

 <span data-ttu-id="6cf93-129">Aby włączyć niestandardowy token zabezpieczający w programie WCF, Utwórz reprezentację obiektu niestandardowego tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="6cf93-129">To enable a custom security token in WCF, create an object representation of the custom security token.</span></span> <span data-ttu-id="6cf93-130">Przykład zawiera tę reprezentację w `CreditCardToken` klasie.</span><span class="sxs-lookup"><span data-stu-id="6cf93-130">The sample has this representation in the `CreditCardToken` class.</span></span> <span data-ttu-id="6cf93-131">Reprezentacja obiektu jest odpowiedzialna za przechowywanie wszystkich istotnych informacji o tokenie zabezpieczającym oraz zawiera listę kluczy zabezpieczeń zawartych w tokenie zabezpieczającym.</span><span class="sxs-lookup"><span data-stu-id="6cf93-131">The object representation is responsible for holding all relevant security token information and to provide a list of security keys contained in the security token.</span></span> <span data-ttu-id="6cf93-132">W takim przypadku token zabezpieczający karty kredytowej nie zawiera klucza zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6cf93-132">In this case, the credit card security token does not contain any security key.</span></span>

 <span data-ttu-id="6cf93-133">W następnej sekcji opisano, co należy zrobić, aby umożliwić przesyłanie tokenów niestandardowych za pośrednictwem sieci i zużywanych przez punkt końcowy WCF.</span><span class="sxs-lookup"><span data-stu-id="6cf93-133">The next section describes what must be done to enable a custom token to be transmitted over the wire and consumed by a WCF endpoint.</span></span>

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

## <a name="getting-the-custom-credit-card-token-to-and-from-the-message"></a><span data-ttu-id="6cf93-134">Pobieranie niestandardowego tokenu karty kredytowej do i z wiadomości</span><span class="sxs-lookup"><span data-stu-id="6cf93-134">Getting the Custom Credit Card Token to and from the Message</span></span>

 <span data-ttu-id="6cf93-135">Serializatory tokenów zabezpieczających w programie WCF są odpowiedzialne za tworzenie reprezentacji obiektów tokenów zabezpieczających na podstawie kodu XML w komunikacie i Tworzenie formularza XML tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6cf93-135">Security token serializers in WCF are responsible for creating an object representation of security tokens from the XML in the message and creating a XML form of the security tokens.</span></span> <span data-ttu-id="6cf93-136">Są one również odpowiedzialne za inne funkcje, takie jak odczytywanie i zapisywanie identyfikatorów kluczy wskazujących tokeny zabezpieczające, ale w tym przykładzie są stosowane tylko funkcje dotyczące tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6cf93-136">They are also responsible for other functionality such as reading and writing key identifiers pointing to security tokens, but this example uses only security token-related functionality.</span></span> <span data-ttu-id="6cf93-137">Aby włączyć Token niestandardowy, należy zaimplementować własny Serializator tokenu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6cf93-137">To enable a custom token you must implement your own security token serializer.</span></span> <span data-ttu-id="6cf93-138">Ten przykład używa `CreditCardSecurityTokenSerializer` klasy do tego celu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-138">This sample uses the `CreditCardSecurityTokenSerializer` class for this purpose.</span></span>

 <span data-ttu-id="6cf93-139">W usłudze, serializator niestandardowy odczytuje formę XML niestandardowego tokenu i tworzy reprezentację niestandardowego obiektu tokena.</span><span class="sxs-lookup"><span data-stu-id="6cf93-139">On the service, the custom serializer reads the XML form of the custom token and creates the custom token object representation from it.</span></span>

 <span data-ttu-id="6cf93-140">Na kliencie `CreditCardSecurityTokenSerializer` Klasa zapisuje informacje zawarte w reprezentacji obiektu tokenu zabezpieczającego w składniku zapisywania XML.</span><span class="sxs-lookup"><span data-stu-id="6cf93-140">On the client, the `CreditCardSecurityTokenSerializer` class writes the information contained in the security token object representation into the XML writer.</span></span>

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

## <a name="how-token-provider-and-token-authenticator-classes-are-created"></a><span data-ttu-id="6cf93-141">Jak są tworzone klasy dostawcy tokenów i wystawców tokenów</span><span class="sxs-lookup"><span data-stu-id="6cf93-141">How Token Provider and Token Authenticator Classes are Created</span></span>

 <span data-ttu-id="6cf93-142">Poświadczenia klienta i usługi są odpowiedzialne za dostarczanie wystąpienia Menedżera tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="6cf93-142">Client and service credentials are responsible for providing the security token manager instance.</span></span> <span data-ttu-id="6cf93-143">Wystąpienie Menedżera tokenów zabezpieczeń służy do uzyskiwania dostawców tokenów, wystawców tokenów i serializatorów tokenów.</span><span class="sxs-lookup"><span data-stu-id="6cf93-143">The security token manager instance is used to get token providers, token authenticators and token serializers.</span></span>

 <span data-ttu-id="6cf93-144">Dostawca tokenów tworzy reprezentację obiektu tokenu na podstawie informacji zawartych w poświadczeniach klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-144">The token provider creates an object representation of the token based on the information contained in the client or service credentials.</span></span> <span data-ttu-id="6cf93-145">Reprezentacja obiektu tokenu jest następnie zapisywana w komunikacie przy użyciu serializatora tokenu (omówione w poprzedniej sekcji).</span><span class="sxs-lookup"><span data-stu-id="6cf93-145">The token object representation is then written to the message using the token serializer (discussed in the previous section).</span></span>

 <span data-ttu-id="6cf93-146">Wystawca uwierzytelnienia tokenu sprawdza poprawność tokenów, które dotarły do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="6cf93-146">The token authenticator validates tokens that arrive in the message.</span></span> <span data-ttu-id="6cf93-147">Reprezentacja obiektu tokenu przychodzącego jest tworzona przez Serializator tokenu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-147">The incoming token object representation is created by the token serializer.</span></span> <span data-ttu-id="6cf93-148">Ta reprezentacja obiektu jest następnie przenoszona do uwierzytelniania tokenów w celu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-148">This object representation is then passed to the token authenticator for validation.</span></span> <span data-ttu-id="6cf93-149">Po pomyślnym sprawdzeniu tokenu wystawca uwierzytelnienia zwraca kolekcję `IAuthorizationPolicy` obiektów reprezentujących informacje zawarte w tokenie.</span><span class="sxs-lookup"><span data-stu-id="6cf93-149">After the token is successfully validated, the token authenticator returns a collection of `IAuthorizationPolicy` objects that represent the information contained in the token.</span></span> <span data-ttu-id="6cf93-150">Te informacje są używane później podczas przetwarzania komunikatów w celu podejmowania decyzji dotyczących autoryzacji i dostarczania oświadczeń dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-150">This information is used later during the message processing to perform authorization decisions and to provide claims for the application.</span></span> <span data-ttu-id="6cf93-151">W tym przykładzie token karty kredytowej używa `CreditCardTokenAuthorizationPolicy` do tego celu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-151">In this example, the credit card token authenticator uses `CreditCardTokenAuthorizationPolicy` for this purpose.</span></span>

 <span data-ttu-id="6cf93-152">Serializator tokenu jest odpowiedzialny za pobieranie obiektu reprezentacji tokenu do i z sieci.</span><span class="sxs-lookup"><span data-stu-id="6cf93-152">The token serializer is responsible for getting the object representation of the token to and from the wire.</span></span> <span data-ttu-id="6cf93-153">Zostało to omówione w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-153">This is discussed in the previous section.</span></span>

 <span data-ttu-id="6cf93-154">W tym przykładzie używamy dostawcy tokenów tylko na kliencie i uwierzytelniającego tokena tylko do usługi, ponieważ chcemy przesłać token karty kredytowej tylko w kierunku od klienta do usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-154">In this sample, we use a token provider only on the client and a token authenticator only on the service, because we want to transmit a credit card token only in the client-to-service direction.</span></span>

 <span data-ttu-id="6cf93-155">Funkcje klienta znajdują się w `CreditCardClientCredentials` `CreditCardClientCredentialsSecurityTokenManager` klasach i `CreditCardTokenProvider` .</span><span class="sxs-lookup"><span data-stu-id="6cf93-155">The functionality on the client is located in the `CreditCardClientCredentials`, `CreditCardClientCredentialsSecurityTokenManager` and `CreditCardTokenProvider` classes.</span></span>

 <span data-ttu-id="6cf93-156">`CreditCardServiceCredentials`W usłudze funkcje znajdują się w klasach `CreditCardTokenAuthenticator` , `CreditCardServiceCredentialsSecurityTokenManager`i `CreditCardTokenAuthorizationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="6cf93-156">On the service, the functionality resides in the `CreditCardServiceCredentials`, `CreditCardServiceCredentialsSecurityTokenManager`, `CreditCardTokenAuthenticator` and `CreditCardTokenAuthorizationPolicy` classes.</span></span>

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

## <a name="displaying-the-callers-information"></a><span data-ttu-id="6cf93-157">Wyświetlanie informacji o wywołujących</span><span class="sxs-lookup"><span data-stu-id="6cf93-157">Displaying the Callers' Information</span></span>

 <span data-ttu-id="6cf93-158">Aby wyświetlić informacje o wywołującym, użyj `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` , jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6cf93-158">To display the caller's information, use the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` as shown in the following sample code.</span></span> <span data-ttu-id="6cf93-159">`ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` Zawiera oświadczenia autoryzacji skojarzone z bieżącym obiektem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="6cf93-159">The `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contains authorization claims associated with the current caller.</span></span> <span data-ttu-id="6cf93-160">Oświadczenia są dostarczane przez `CreditCardToken` klasę w swojej `AuthorizationPolicies` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-160">The claims are supplied by the `CreditCardToken` class in its `AuthorizationPolicies` collection.</span></span>

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

 <span data-ttu-id="6cf93-161">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf93-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6cf93-162">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-162">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="6cf93-163">Plik wsadowy konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6cf93-163">Setup Batch File</span></span>

 <span data-ttu-id="6cf93-164">Plik wsadowy Setup. bat dołączony do tego przykładu umożliwia skonfigurowanie serwera z odpowiednimi certyfikatami w celu uruchomienia aplikacji hostowanej przez usługi IIS, która wymaga zabezpieczeń opartych na certyfikatach serwera.</span><span class="sxs-lookup"><span data-stu-id="6cf93-164">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run the IIS-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="6cf93-165">Ten plik wsadowy należy zmodyfikować, aby mógł działać na różnych komputerach lub działać w nieobsługiwanym przypadku.</span><span class="sxs-lookup"><span data-stu-id="6cf93-165">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="6cf93-166">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych, dzięki czemu można je zmodyfikować tak, aby były uruchamiane w odpowiedniej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-166">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="6cf93-167">Tworzenie certyfikatu serwera:</span><span class="sxs-lookup"><span data-stu-id="6cf93-167">Creating the server certificate:</span></span>

     <span data-ttu-id="6cf93-168">Poniższe wiersze z `Setup.bat` pliku wsadowego tworzą certyfikat serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="6cf93-168">The following lines from the `Setup.bat` batch file create the server certificate to be used.</span></span> <span data-ttu-id="6cf93-169">`%SERVER_NAME%` Zmienna określa nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="6cf93-169">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="6cf93-170">Zmień tę zmienną, aby określić własną nazwę serwera.</span><span class="sxs-lookup"><span data-stu-id="6cf93-170">Change this variable to specify your own server name.</span></span> <span data-ttu-id="6cf93-171">Wartość domyślna w tym pliku wsadowym to localhost.</span><span class="sxs-lookup"><span data-stu-id="6cf93-171">The default in this batch file is localhost.</span></span> <span data-ttu-id="6cf93-172">Jeśli zmienisz `%SERVER_NAME%` zmienną, musisz przejść przez pliki Client.cs i Service.cs i zamienić wszystkie wystąpienia localhost na nazwę serwera używaną w skrypcie Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="6cf93-172">If you change the `%SERVER_NAME%` variable, you must go through the Client.cs and Service.cs files and replace all instances of localhost with the server name that you use in the Setup.bat script.</span></span>

     <span data-ttu-id="6cf93-173">Certyfikat jest przechowywany w magazynie `LocalMachine` (Personal) w lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-173">The certificate is stored in My (Personal) store under the `LocalMachine` store location.</span></span> <span data-ttu-id="6cf93-174">Certyfikat jest przechowywany w magazynie LocalMachine dla usług hostowanych przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="6cf93-174">The certificate is stored in the LocalMachine store for the IIS-hosted services.</span></span> <span data-ttu-id="6cf93-175">W przypadku usług samodzielnych należy zmodyfikować plik wsadowy, aby przechowywać certyfikat klienta w lokalizacji magazynu CurrentUser przez zastąpienie ciągu LocalMachine ciągiem CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6cf93-175">For self-hosted services, you should modify the batch file to store the client certificate in the CurrentUser store location by replacing the string LocalMachine with CurrentUser.</span></span>

    ```
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6cf93-176">Instalowanie certyfikatu serwera w magazynie zaufanych certyfikatów klienta:</span><span class="sxs-lookup"><span data-stu-id="6cf93-176">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="6cf93-177">Następujące wiersze w pliku wsadowym Setup. bat kopiują certyfikat serwera do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf93-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6cf93-178">Ten krok jest wymagany, ponieważ certyfikaty wygenerowane przez Makecert. exe nie są niejawnie zaufane przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf93-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6cf93-179">Jeśli masz już certyfikat, który znajduje się w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten krok zapełniania magazynu certyfikatów klienta z certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="6cf93-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    echo ************
    echo copying server cert to client's TrustedPeople store
    echo ************
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="6cf93-180">Aby umożliwić dostęp do klucza prywatnego certyfikatu z usługi hostowanej przez usługi IIS, konto użytkownika, pod którym działa proces hostowany przez usługi IIS, musi mieć przyznane odpowiednie uprawnienia do klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="6cf93-180">To enable access to the certificate private key from the IIS-hosted service, the user account under which the IIS-hosted process is running must be granted appropriate permissions for the private key.</span></span> <span data-ttu-id="6cf93-181">Jest to realizowane przez ostatnie kroki skryptu Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="6cf93-181">This is accomplished by last steps in the Setup.bat script.</span></span>

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
> <span data-ttu-id="6cf93-182">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6cf93-182">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="6cf93-183">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="6cf93-183">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="6cf93-184">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="6cf93-184">To set up and build the sample</span></span>

1. <span data-ttu-id="6cf93-185">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cf93-185">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6cf93-186">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6cf93-186">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6cf93-187">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="6cf93-187">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6cf93-188">Otwórz okno wiersza polecenia programu Visual Studio 2012 z uprawnieniami administratora i uruchom setup. bat z przykładowego folderu instalacji.</span><span class="sxs-lookup"><span data-stu-id="6cf93-188">Open a Visual Studio 2012 Command Prompt window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="6cf93-189">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu. Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert. exe.</span><span class="sxs-lookup"><span data-stu-id="6cf93-189">This installs all the certificates required for running the sample.Make sure that the path includes the folder where Makecert.exe is located.</span></span>

> [!NOTE]
> <span data-ttu-id="6cf93-190">Pamiętaj o usunięciu certyfikatów, uruchamiając Oczyść. bat po zakończeniu z przykładem.</span><span class="sxs-lookup"><span data-stu-id="6cf93-190">Be sure to remove the certificates by running Cleanup.bat when finished with the sample.</span></span> <span data-ttu-id="6cf93-191">Inne przykłady zabezpieczeń używają tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="6cf93-191">Other security samples use the same certificates.</span></span>  
  
1. <span data-ttu-id="6cf93-192">Uruchom plik Client. exe z katalogu client\bin.</span><span class="sxs-lookup"><span data-stu-id="6cf93-192">Launch Client.exe from client\bin directory.</span></span> <span data-ttu-id="6cf93-193">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf93-193">Client activity is displayed on the client console application.</span></span>  
  
2. <span data-ttu-id="6cf93-194">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6cf93-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computer"></a><span data-ttu-id="6cf93-195">Aby uruchomić przykład na komputerze</span><span class="sxs-lookup"><span data-stu-id="6cf93-195">To run the sample across computer</span></span>  
  
1. <span data-ttu-id="6cf93-196">Utwórz katalog na komputerze usługi dla plików binarnych usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-196">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="6cf93-197">Skopiuj pliki programu Service Files do katalogu usługi na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-197">Copy the service program files into the service directory on the service computer.</span></span> <span data-ttu-id="6cf93-198">Nie zapomnij skopiować CreditCardFile. txt; w przeciwnym razie wystawca uwierzytelnienia karty kredytowej nie może zweryfikować informacji o karcie kredytowej wysłanych przez klienta.</span><span class="sxs-lookup"><span data-stu-id="6cf93-198">Do not forget to copy CreditCardFile.txt; otherwise the credit card authenticator cannot validate credit card information sent from the client.</span></span> <span data-ttu-id="6cf93-199">Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-199">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="6cf93-200">Musisz mieć certyfikat serwera z nazwą podmiotu zawierającą w pełni kwalifikowaną nazwę domeny komputera.</span><span class="sxs-lookup"><span data-stu-id="6cf93-200">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="6cf93-201">Można go utworzyć przy użyciu Setup. bat, jeśli zmienisz `%SERVER_NAME%` zmienną na w pełni kwalifikowaną nazwę komputera, na którym usługa jest hostowana.</span><span class="sxs-lookup"><span data-stu-id="6cf93-201">You can create one using the Setup.bat if you change the `%SERVER_NAME%` variable to fully-qualified name of the computer where the service is hosted.</span></span> <span data-ttu-id="6cf93-202">Należy pamiętać, że plik Setup. bat musi być uruchamiany w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="6cf93-202">Note that the Setup.bat file must be run in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="6cf93-203">Skopiuj certyfikat serwera do magazynu CurrentUser-TrustedPeople na kliencie.</span><span class="sxs-lookup"><span data-stu-id="6cf93-203">Copy the server certificate into the CurrentUser-TrustedPeople store on the client.</span></span> <span data-ttu-id="6cf93-204">Należy to zrobić tylko wtedy, gdy certyfikat serwera nie zostanie wystawiony przez zaufanego wystawcy.</span><span class="sxs-lookup"><span data-stu-id="6cf93-204">You must do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="6cf93-205">W pliku EchoServiceHost.cs Zmień wartość w polu Nazwa podmiotu certyfikatu, aby określić w pełni kwalifikowaną nazwę komputera zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="6cf93-205">In the EchoServiceHost.cs file, change the value of the certificate subject name to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="6cf93-206">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputera klienckiego.</span><span class="sxs-lookup"><span data-stu-id="6cf93-206">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
7. <span data-ttu-id="6cf93-207">W pliku Client.cs Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="6cf93-207">In the Client.cs file, change the address value of the endpoint to match the new address of your service.</span></span>  
  
8. <span data-ttu-id="6cf93-208">W pliku Client.cs Zmień nazwę podmiotu certyfikatu X. 509 usługi w taki sposób, aby była zgodna z w pełni kwalifikowaną nazwą komputera hosta zdalnego zamiast localhost.</span><span class="sxs-lookup"><span data-stu-id="6cf93-208">In the Client.cs file change the subject name of the service X.509 certificate to match the fully-qualified computer name of the remote host instead of localhost.</span></span>  
  
9. <span data-ttu-id="6cf93-209">Na komputerze klienckim uruchom program Client. exe w oknie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="6cf93-209">On the client computer, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="6cf93-210">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6cf93-210">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6cf93-211">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="6cf93-211">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="6cf93-212">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="6cf93-212">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
