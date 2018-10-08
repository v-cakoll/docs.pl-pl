---
title: Współdziałanie z aplikacjami POX
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: b7fdb4e16bce52025515ced065d0f48cffb7fa3f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850091"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="1cf30-102">Współdziałanie z aplikacjami POX</span><span class="sxs-lookup"><span data-stu-id="1cf30-102">Interoperability with POX applications</span></span>

<span data-ttu-id="1cf30-103">"Zwykłe stare XML" aplikacji (POX) komunikują się przez wymianę nieprzetworzone komunikaty HTTP, które zawierają tylko dane aplikacji XML, który nie jest ujęty w kopercie SOAP.</span><span class="sxs-lookup"><span data-stu-id="1cf30-103">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="1cf30-104">Windows Communication Foundation (WCF) może zapewnić zarówno w przypadku usług, jak i klientów, którzy używają POX wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1cf30-104">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="1cf30-105">W usłudze WCF może służyć do implementowania usług, które uwidaczniają punkty końcowe do klientów, takich jak przeglądarki sieci Web i języków skryptów, które wysyłania i odbierania komunikatów POX.</span><span class="sxs-lookup"><span data-stu-id="1cf30-105">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="1cf30-106">Na komputerze klienckim model programowania WCF może służyć do wdrożenia klientów komunikujących się za pomocą usług opartych na POX.</span><span class="sxs-lookup"><span data-stu-id="1cf30-106">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cf30-107">W tym dokumencie pierwotnie został napisany dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span><span class="sxs-lookup"><span data-stu-id="1cf30-107">This document was originally written for the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0.</span></span>  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] <span data-ttu-id="1cf30-108">3.5 ma wbudowaną obsługę pracy z aplikacjami POX.</span><span class="sxs-lookup"><span data-stu-id="1cf30-108"> 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="1cf30-109">Aby uzyskać więcej informacji na temat, zobacz [modelu programowania protokołu HTTP sieci Web programu WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span><span class="sxs-lookup"><span data-stu-id="1cf30-109">For more information about see [WCF Web HTTP Programming Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="1cf30-110">POX programowania przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="1cf30-110">POX programming with WCF</span></span>

<span data-ttu-id="1cf30-111">Usługi WCF, które komunikują się za pośrednictwem protokołu HTTP przy użyciu wiadomości POX [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="1cf30-111">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="1cf30-112">To niestandardowe powiązanie zawiera dwa elementy:</span><span class="sxs-lookup"><span data-stu-id="1cf30-112">This custom binding contains two elements:</span></span>

- [<span data-ttu-id="1cf30-113">\<httpTransport ></span><span class="sxs-lookup"><span data-stu-id="1cf30-113">\<httpTransport></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)

- [<span data-ttu-id="1cf30-114">\<textMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="1cf30-114">\<textMessageEncoding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="1cf30-115">Standardowa koder komunikatu tekstowego WCF specjalnie jest skonfigurowany do używania <xref:System.ServiceModel.Channels.MessageVersion.None%2A> wartość, która pozwala na przetwarzanie XML komunikat ładunków pojawiające się nie opakowane w kopercie SOAP.</span><span class="sxs-lookup"><span data-stu-id="1cf30-115">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="1cf30-116">Klienci WCF, które komunikują się za pośrednictwem protokołu HTTP przy użyciu komunikatów o POX użyć podobnych powiązania (pokazano w poniższym kodzie imperatywne).</span><span class="sxs-lookup"><span data-stu-id="1cf30-116">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

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

<span data-ttu-id="1cf30-117">Ponieważ klienci POX należy jawnie określić identyfikatory URI, do którego wysyłają komunikaty, są zazwyczaj należy skonfigurować <xref:System.ServiceModel.Channels.HttpTransportBindingElement> trybu ręcznego adresowania, ustawiając <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> właściwości `true` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="1cf30-117">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="1cf30-118">Dzięki temu wiadomości należy się zająć jawnie przez kod aplikacji i nie jest konieczne utworzyć nowy <xref:System.ServiceModel.ChannelFactory> za każdym razem, gdy aplikacja wysyła komunikat do inny identyfikator URI protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cf30-118">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="1cf30-119">Ponieważ w celu przekazania informacji o protokole ważne wiadomości POX nie używają nagłówków protokołu SOAP, POX klientów i usług w często muszą manipulować rodzajów podstawowego żądania HTTP używany do wysyłania i odbierania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="1cf30-119">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="1cf30-120">Informacje protokołu specyficzne dla protokołu HTTP, takie jak nagłówki HTTP i kodów stanu są udostępniane w modelu programowania usług WCF za pomocą dwóch klas:</span><span class="sxs-lookup"><span data-stu-id="1cf30-120">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="1cf30-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, który zawiera informacje o żądaniu HTTP, takich jak nagłówki metodę i żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cf30-121"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="1cf30-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, który zawiera informacje o odpowiedzi HTTP, takich jak opis kodu i stan stanu HTTP, a także wszystkie nagłówki odpowiedzi HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cf30-122"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="1cf30-123">Poniższy przykład kodu pokazuje sposób tworzenia komunikatu żądania HTTP GET, które są skierowane do `http://localhost:8100/customers`.</span><span class="sxs-lookup"><span data-stu-id="1cf30-123">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="1cf30-124">Po pierwsze, puste żądanie <xref:System.ServiceModel.Channels.Message> jest tworzony przez wywołanie <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="1cf30-124">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="1cf30-125"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> Parametr jest używany do wskazania, że koperty protokołu SOAP nie jest wymagany i <xref:System.String.Empty> parametr jest przekazywany jako akcję.</span><span class="sxs-lookup"><span data-stu-id="1cf30-125">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="1cf30-126">Komunikat żądania jest następnie rozwiązane przez ustawienie <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> nagłówka do żądanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="1cf30-126">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="1cf30-127">Następnie <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> jest tworzony i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> jest ustawiona na zlecenie HTTP metody GET i <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> jest ustawiona na `true` do wskazania, że żadne dane nie powinny być wysyłane w treści wychodzący komunikat żądania HTTP.</span><span class="sxs-lookup"><span data-stu-id="1cf30-127">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="1cf30-128">Na koniec właściwości żądania zostanie dodany do <xref:System.ServiceModel.Channels.Message.Properties%2A> zbiór komunikat żądania, aby go mogą mieć wpływ na sposób transportu HTTP wysyła żądanie.</span><span class="sxs-lookup"><span data-stu-id="1cf30-128">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="1cf30-129">Komunikat jest gotowy do wysłania przez odpowiednie wystąpienie <xref:System.ServiceModel.Channels.IRequestChannel>.</span><span class="sxs-lookup"><span data-stu-id="1cf30-129">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="1cf30-130">Podobne techniki może służyć w usłudze można wyodrębnić <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> z przychodzących wiadomości i konstrukcji odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="1cf30-130">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
