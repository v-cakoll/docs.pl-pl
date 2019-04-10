---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 84a5bc763f898b3d323a6cee468c6e22d27d85a0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229605"
---
# <a name="udpbinding"></a><span data-ttu-id="b8623-101">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="b8623-101">\<udpBinding></span></span>
<span data-ttu-id="b8623-102">Element konfiguracji umożliwiają skonfigurowanie <xref:System.ServiceModel.UdpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8623-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="b8623-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8623-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8623-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b8623-104">\<bindings></span></span>  
<span data-ttu-id="b8623-105">\<udpBinding></span><span class="sxs-lookup"><span data-stu-id="b8623-105">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8623-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8623-106">Syntax</span></span>  
  
```xml  
<udpBinding>
  <binding closeTimeout="TimeSpan"
           duplicateMessageHistoryLength="Integer"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxPendingMessagesTotalSize="Integer"
           maxReceivedMessageSize="Integer"
           maxRetransmitCount="Integer"
           multicastInterfaceId="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           timeToLive="TimeSpan">
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8623-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b8623-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b8623-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b8623-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8623-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b8623-109">Attributes</span></span>  
  
|<span data-ttu-id="b8623-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b8623-110">Attribute</span></span>|<span data-ttu-id="b8623-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b8623-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="b8623-112">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="b8623-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b8623-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b8623-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8623-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b8623-114">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="b8623-115">Wartość całkowita, określająca długość historii zduplikowany komunikat.</span><span class="sxs-lookup"><span data-stu-id="b8623-115">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="b8623-116">Wartość całkowitą, która określa maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="b8623-116">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="b8623-117">Wartość domyślna to 524288 (0x80000) bajtów.</span><span class="sxs-lookup"><span data-stu-id="b8623-117">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="b8623-118">Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania na punkt końcowy skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="b8623-118">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="b8623-119">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b8623-119">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="b8623-120">Wartość całkowita określająca maksymalną liczbę komunikatów odebranych, ale nie zostały jeszcze usunięte z kolejką wejściową dla wystąpienia pojedynczy kanał.</span><span class="sxs-lookup"><span data-stu-id="b8623-120">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="b8623-121">Dodatnia liczba całkowita określająca maksymalny rozmiar komunikatu, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowany tym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="b8623-121">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b8623-122">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="b8623-122">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="b8623-123">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b8623-123">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b8623-124">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b8623-124">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="b8623-125">Wartość całkowita określająca maksymalną liczbę wiadomości retransmisji.</span><span class="sxs-lookup"><span data-stu-id="b8623-125">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="b8623-126">Wartość całkowitą, która określa identyfikator interfejsu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="b8623-126">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="b8623-127">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="b8623-127">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b8623-128">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="b8623-128">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b8623-129">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="b8623-129">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="b8623-130">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="b8623-130">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="b8623-131">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="b8623-131">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b8623-132">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b8623-132">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="b8623-133">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="b8623-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b8623-134">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b8623-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8623-135">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b8623-135">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="b8623-136">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="b8623-136">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b8623-137">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b8623-137">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8623-138">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b8623-138">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="b8623-139">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="b8623-139">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b8623-140">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b8623-140">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b8623-141">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b8623-141">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="b8623-142">Określa kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="b8623-142">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b8623-143">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="b8623-143">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b8623-144">-BigEndianUnicode: Unicode BigEndian kodowania.</span><span class="sxs-lookup"><span data-stu-id="b8623-144">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="b8623-145">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="b8623-145">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="b8623-146">-   UTF8: 8-bitowego kodowania</span><span class="sxs-lookup"><span data-stu-id="b8623-146">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b8623-147">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="b8623-147">The default is UTF8.</span></span> <span data-ttu-id="b8623-148">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b8623-148">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="b8623-149">Wartość przedziału czasu, który określa czas wygaśnięcia dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="b8623-149">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8623-150">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b8623-150">Child Elements</span></span>  
  
|<span data-ttu-id="b8623-151">Element</span><span class="sxs-lookup"><span data-stu-id="b8623-151">Element</span></span>|<span data-ttu-id="b8623-152">Opis</span><span class="sxs-lookup"><span data-stu-id="b8623-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8623-153">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b8623-153">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="b8623-154">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="b8623-154">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b8623-155">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b8623-155">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b8623-156">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b8623-156">Parent Elements</span></span>  
  
|<span data-ttu-id="b8623-157">Element</span><span class="sxs-lookup"><span data-stu-id="b8623-157">Element</span></span>|<span data-ttu-id="b8623-158">Opis</span><span class="sxs-lookup"><span data-stu-id="b8623-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8623-159">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b8623-159">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b8623-160">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="b8623-160">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8623-161">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8623-161">Remarks</span></span>  
 <span data-ttu-id="b8623-162">UdpBinding umożliwia usługom WCF do komunikowania się za pomocą transportu UDP.</span><span class="sxs-lookup"><span data-stu-id="b8623-162">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="b8623-163">Umożliwia ona "fire and forget" wymianę komunikatów, gdy klient wysyła komunikat do usługi i oczekuje, że nie odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b8623-163">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8623-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8623-164">Example</span></span>  
 <span data-ttu-id="b8623-165">Poniższy przykład przedstawia sposób konfigurowania <xref:System.ServiceModel.UdpBinding> przy użyciu <`udpBinding`> element.</span><span class="sxs-lookup"><span data-stu-id="b8623-165">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
```xml  
<udpBinding>
  <binding  closeTimeout="00:10:00"
            duplicateMessageHistoryLength="100"
            maxBufferPoolSize="100"
            maxPendingMessagesTotalSize="100000"
            maxReceivedMessageSize="65536"
            maxRetransmitCount="10"
            multicastInterfaceId="00000"
            name="myUdpBinding"
            openTimeout="00:10:00"
            receiveTimeout="00:10:00"
            sendTimeout="00:10:00"
            textEncoding="utf-8"
            timeToLive="00:10:00">
    <readerQuotas />
  </binding>
</udpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="b8623-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8623-166">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="b8623-167">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b8623-167">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b8623-168">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="b8623-168">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b8623-169">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="b8623-169">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b8623-170">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b8623-170">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
