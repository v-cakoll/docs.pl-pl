---
title: <udpBinding>
ms.date: 03/30/2017
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
ms.openlocfilehash: 7fa72d233d6489ab6a2c534f69c66a55a22d0f59
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74429833"
---
# \<udpBinding>
<span data-ttu-id="f6d27-101">Element konfiguracji służący do konfigurowania <xref:System.ServiceModel.UdpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-101">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="f6d27-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6d27-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6d27-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f6d27-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f6d27-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f6d27-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6d27-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f6d27-105">Attributes</span></span>  
  
|<span data-ttu-id="f6d27-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f6d27-106">Attribute</span></span>|<span data-ttu-id="f6d27-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d27-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f6d27-108"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="f6d27-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f6d27-109">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="f6d27-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6d27-110">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6d27-110">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="f6d27-111">Wartość całkowita określająca zduplikowaną długość historii komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f6d27-111">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="f6d27-112">Wartość całkowita określająca maksymalną ilość pamięci przydzieloną do użytku przez Menedżera buforów komunikatów, które odbierają komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="f6d27-112">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="f6d27-113">Wartość domyślna to 524288 (0x80000) b.</span><span class="sxs-lookup"><span data-stu-id="f6d27-113">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="f6d27-114">Wartość całkowita, która określa maksymalny rozmiar bufora, w bajtach, który przechowuje komunikaty podczas przetwarzania dla punktu końcowego skonfigurowanego za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-114">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="f6d27-115">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="f6d27-115">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="f6d27-116">Wartość całkowita określająca maksymalną liczbę odebranych komunikatów, które nie zostały jeszcze usunięte z kolejki wejściowej dla wystąpienia poszczególnych kanałów.</span><span class="sxs-lookup"><span data-stu-id="f6d27-116">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="f6d27-117">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, w tym nagłówki, dla wiadomości, które można odbierać w kanale skonfigurowanym za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-117">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f6d27-118">Nadawca odbiera błąd protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="f6d27-118">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="f6d27-119">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f6d27-119">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f6d27-120">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="f6d27-120">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="f6d27-121">Wartość całkowita określająca maksymalną liczbę przesyłanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f6d27-121">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="f6d27-122">Wartość całkowita określająca identyfikator interfejsu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="f6d27-122">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="f6d27-123">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-123">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f6d27-124">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-124">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f6d27-125">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="f6d27-125">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f6d27-126">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f6d27-126">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f6d27-127"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="f6d27-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f6d27-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="f6d27-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6d27-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6d27-129">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f6d27-130">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="f6d27-130">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f6d27-131">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="f6d27-131">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6d27-132">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f6d27-132">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f6d27-133"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f6d27-134">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="f6d27-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f6d27-135">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f6d27-135">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="f6d27-136">Ustawia kodowanie zestawu znaków, który ma być używany do emitowania komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="f6d27-136">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="f6d27-137">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f6d27-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6d27-138">-BigEndianUnicode: kodowanie Unicode BigEndian.</span><span class="sxs-lookup"><span data-stu-id="f6d27-138">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="f6d27-139">-Unicode: kodowanie 16-bitowe.</span><span class="sxs-lookup"><span data-stu-id="f6d27-139">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="f6d27-140">-UTF8: kodowanie 8-bitowe</span><span class="sxs-lookup"><span data-stu-id="f6d27-140">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="f6d27-141">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="f6d27-141">The default is UTF8.</span></span> <span data-ttu-id="f6d27-142">Ten atrybut jest typu <xref:System.Text.Encoding> .</span><span class="sxs-lookup"><span data-stu-id="f6d27-142">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="f6d27-143">Wartość TimeSpan określająca czas wygaśnięcia powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-143">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6d27-144">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f6d27-144">Child Elements</span></span>  
  
|<span data-ttu-id="f6d27-145">Element</span><span class="sxs-lookup"><span data-stu-id="f6d27-145">Element</span></span>|<span data-ttu-id="f6d27-146">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d27-146">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="f6d27-147">Definiuje ograniczenia złożoności komunikatów protokołu SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f6d27-147">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f6d27-148">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="f6d27-148">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6d27-149">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f6d27-149">Parent Elements</span></span>  
  
|<span data-ttu-id="f6d27-150">Element</span><span class="sxs-lookup"><span data-stu-id="f6d27-150">Element</span></span>|<span data-ttu-id="f6d27-151">Opis</span><span class="sxs-lookup"><span data-stu-id="f6d27-151">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="f6d27-152">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="f6d27-152">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6d27-153">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6d27-153">Remarks</span></span>  
 <span data-ttu-id="f6d27-154">UdpBinding umożliwia usługom WCF komunikowanie się za pośrednictwem transportu UDP.</span><span class="sxs-lookup"><span data-stu-id="f6d27-154">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="f6d27-155">Umożliwia ona wymianę komunikatów "Fire" i "zapomnij", gdy klient wysyła komunikat do usługi i oczekuje braku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f6d27-155">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6d27-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6d27-156">Example</span></span>  
 <span data-ttu-id="f6d27-157">Poniższy przykład pokazuje, jak skonfigurować <xref:System.ServiceModel.UdpBinding> przy użyciu <`udpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="f6d27-157">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6d27-158">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6d27-158">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="f6d27-159">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f6d27-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f6d27-160">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f6d27-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f6d27-161">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f6d27-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
