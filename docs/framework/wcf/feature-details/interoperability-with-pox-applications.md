---
title: Współdziałanie z aplikacjami POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 64a6d850a32b14bc60cd43466e04b53a7a39be81
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579270"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="8ea6e-102">Współdziałanie z aplikacjami POX</span><span class="sxs-lookup"><span data-stu-id="8ea6e-102">Interoperability with POX applications</span></span>

<span data-ttu-id="8ea6e-103">"Zwykłe stare aplikacje XML" (POX) komunikują się przez wymianę nieprzetworzonych komunikatów HTTP, które zawierają tylko dane aplikacji XML, które nie są ujęte w kopercie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="8ea6e-104">Windows Communication Foundation (WCF) może zapewnić zarówno usługi, jak i klientów korzystających z komunikatów POX.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="8ea6e-105">Usługa WCF może służyć do implementowania usług, które ujawniają punkty końcowe klientom, takim jak przeglądarki sieci Web i języki skryptów, które wysyłają i odbierają wiadomości POX.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="8ea6e-106">Na kliencie model programowania WCF może służyć do implementowania klientów komunikujących się z usługami opartymi na POX.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ea6e-107">Ten dokument został pierwotnie zapisany dla .NET Framework 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-107">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="8ea6e-108">.NET Framework 3,5 ma wbudowaną obsługę pracy z aplikacjami POX.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-108">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="8ea6e-109">Aby uzyskać więcej informacji, zobacz [model programowania HTTP sieci Web](wcf-web-http-programming-model.md)w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-109">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="8ea6e-110">Programowanie POX przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="8ea6e-110">POX programming with WCF</span></span>

<span data-ttu-id="8ea6e-111">Usługi WCF, które komunikują się za pośrednictwem protokołu HTTP przy użyciu komunikatów POX używają usługi [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="8ea6e-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="8ea6e-112">To powiązanie niestandardowe zawiera dwa elementy:</span><span class="sxs-lookup"><span data-stu-id="8ea6e-112">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="8ea6e-113">Standardowy koder wiadomości tekstowych WCF jest specjalnie skonfigurowany do korzystania z <xref:System.ServiceModel.Channels.MessageVersion.None%2A> wartości, co pozwala na przetwarzanie ładunków komunikatów XML, które nie są umieszczane w kopercie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-113">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="8ea6e-114">Klienci programu WCF komunikują się za pośrednictwem protokołu HTTP przy użyciu komunikatów POX używają podobnego powiązania (pokazanego w poniższym kodzie).</span><span class="sxs-lookup"><span data-stu-id="8ea6e-114">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="8ea6e-115">Ponieważ klienci POX muszą jawnie określić identyfikatory URI, do których są wysyłane wiadomości, zazwyczaj muszą skonfigurować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> do trybu ręcznego adresowania, ustawiając właściwość na <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> `true` na element.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-115">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="8ea6e-116">Dzięki temu komunikaty mają być jawnie rozkierowane przez kod aplikacji i nie trzeba tworzyć nowych za <xref:System.ServiceModel.ChannelFactory> każdym razem, gdy aplikacja wysyła komunikat do innego identyfikatora URI protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-116">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="8ea6e-117">Ponieważ komunikaty POX nie używają nagłówków protokołu SOAP do przekazywania ważnych informacji o protokole, POX klienci i usługi często muszą manipulować fragmentami podstawowego żądania HTTP, które są używane do wysyłania lub odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-117">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="8ea6e-118">Informacje o protokole protokołu HTTP, takie jak nagłówki HTTP i kody stanu, są rozmieszczone w modelu programowania WCF przez dwie klasy:</span><span class="sxs-lookup"><span data-stu-id="8ea6e-118">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="8ea6e-119"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, który zawiera informacje na temat żądania HTTP, takie jak metoda HTTP i nagłówki żądania.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-119"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="8ea6e-120"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, który zawiera informacje o odpowiedzi HTTP, takie jak kod stanu HTTP i opis stanu, a także wszystkie nagłówki odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-120"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="8ea6e-121">Poniższy przykład kodu pokazuje, jak utworzyć komunikat żądania HTTP GET, który jest rozkierowany `http://localhost:8100/customers` .</span><span class="sxs-lookup"><span data-stu-id="8ea6e-121">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="8ea6e-122">Najpierw jest tworzone puste żądanie <xref:System.ServiceModel.Channels.Message> przez wywołanie <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29> .</span><span class="sxs-lookup"><span data-stu-id="8ea6e-122">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="8ea6e-123"><xref:System.ServiceModel.Channels.MessageVersion.None%2A>Parametr jest używany do wskazania, że koperta protokołu SOAP nie jest wymagana, a <xref:System.String.Empty> parametr jest przenoszona jako akcja.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-123">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="8ea6e-124">Następnie komunikat żądania jest rozkierowany przez ustawienie <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> nagłówka do żądanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-124">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="8ea6e-125">Następnie <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> jest tworzony i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> ma ustawioną metodę get zlecenia HTTP i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> jest ustawiony na wartość, aby `true` wskazać, że żadne dane nie powinny być wysyłane w treści komunikatu żądania wychodzącego http.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-125">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="8ea6e-126">Na koniec Właściwość żądania jest dodawana do <xref:System.ServiceModel.Channels.Message.Properties%2A> kolekcji komunikatów żądania, co może mieć wpływ na sposób wysyłania żądania przez transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-126">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="8ea6e-127">Wiadomość jest następnie gotowa do wysłania w odpowiednim wystąpieniu <xref:System.ServiceModel.Channels.IRequestChannel> .</span><span class="sxs-lookup"><span data-stu-id="8ea6e-127">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="8ea6e-128">Podobne techniki mogą być używane w usłudze w celu wyodrębnienia <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z komunikatu przychodzącego i skonstruowania odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="8ea6e-128">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
