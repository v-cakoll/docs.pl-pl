---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 95ce89aabb400c01002799fd8251383a2e5dd4c2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732694"
---
# <a name="udpbinding"></a><span data-ttu-id="5c7b4-101">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="5c7b4-101">\<udpBinding></span></span>
<span data-ttu-id="5c7b4-102">Element konfiguracji służący do konfigurowania powiązania <xref:System.ServiceModel.UdpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-102">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
<span data-ttu-id="5c7b4-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5c7b4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5c7b4-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5c7b4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5c7b4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="5c7b4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5c7b4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<udpBinding >**</span><span class="sxs-lookup"><span data-stu-id="5c7b4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c7b4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c7b4-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c7b4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c7b4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c7b4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c7b4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c7b4-110">Attributes</span></span>  
  
|<span data-ttu-id="5c7b4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5c7b4-111">Attribute</span></span>|<span data-ttu-id="5c7b4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5c7b4-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5c7b4-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c7b4-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="5c7b4-116">Wartość całkowita określająca zduplikowaną długość historii komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="5c7b4-117">Wartość całkowita określająca maksymalną ilość pamięci przydzieloną do użytku przez Menedżera buforów komunikatów, które odbierają komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="5c7b4-118">Wartość domyślna to 524288 (0x80000) b.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="5c7b4-119">Wartość całkowita, która określa maksymalny rozmiar bufora, w bajtach, który przechowuje komunikaty podczas przetwarzania dla punktu końcowego skonfigurowanego za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="5c7b4-120">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="5c7b4-121">Wartość całkowita określająca maksymalną liczbę odebranych komunikatów, które nie zostały jeszcze usunięte z kolejki wejściowej dla wystąpienia poszczególnych kanałów.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="5c7b4-122">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, w tym nagłówki, dla wiadomości, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="5c7b4-123">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="5c7b4-124">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5c7b4-125">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="5c7b4-126">Wartość całkowita określająca maksymalną liczbę przesyłanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="5c7b4-127">Wartość całkowita określająca identyfikator interfejsu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="5c7b4-128">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5c7b4-129">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5c7b4-130">Każde powiązanie ma atrybut `name` i `namespace`, który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="5c7b4-131">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="5c7b4-132">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5c7b4-133">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5c7b4-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5c7b4-134">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5c7b4-135">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c7b4-136">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5c7b4-137">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5c7b4-138">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c7b4-139">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5c7b4-140">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5c7b4-141">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5c7b4-142">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="5c7b4-143">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="5c7b4-144">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="5c7b4-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5c7b4-145">-BigEndianUnicode: kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="5c7b4-146">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="5c7b4-147">-UTF8: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="5c7b4-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="5c7b4-148">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-148">The default is UTF8.</span></span> <span data-ttu-id="5c7b4-149">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="5c7b4-150">Wartość TimeSpan określająca czas wygaśnięcia powiązania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c7b4-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c7b4-151">Child Elements</span></span>  
  
|<span data-ttu-id="5c7b4-152">Element</span><span class="sxs-lookup"><span data-stu-id="5c7b4-152">Element</span></span>|<span data-ttu-id="5c7b4-153">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5c7b4-154">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5c7b4-154">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="5c7b4-155">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="5c7b4-156">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c7b4-157">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c7b4-157">Parent Elements</span></span>  
  
|<span data-ttu-id="5c7b4-158">Element</span><span class="sxs-lookup"><span data-stu-id="5c7b4-158">Element</span></span>|<span data-ttu-id="5c7b4-159">Opis</span><span class="sxs-lookup"><span data-stu-id="5c7b4-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c7b4-160">> powiązań\<</span><span class="sxs-lookup"><span data-stu-id="5c7b4-160">\<bindings></span></span>](bindings.md)|<span data-ttu-id="5c7b4-161">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c7b4-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c7b4-162">Remarks</span></span>  
 <span data-ttu-id="5c7b4-163">UdpBinding umożliwia usługom WCF komunikowanie się za pośrednictwem transportu UDP.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="5c7b4-164">Umożliwia ona wymianę komunikatów "Fire" i "zapomnij", gdy klient wysyła komunikat do usługi i oczekuje braku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c7b4-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c7b4-165">Example</span></span>  
 <span data-ttu-id="5c7b4-166">Poniższy przykład pokazuje, jak skonfigurować <xref:System.ServiceModel.UdpBinding> przy użyciu <`udpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="5c7b4-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c7b4-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c7b4-167">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="5c7b4-168">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5c7b4-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c7b4-169">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5c7b4-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c7b4-170">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5c7b4-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5c7b4-171">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="5c7b4-171">\<binding></span></span>](bindings.md)
