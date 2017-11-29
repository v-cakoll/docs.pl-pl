---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8eb4d28885308c400c445ae71019373ec92ed27a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltudpbindinggt"></a><span data-ttu-id="22434-102">&lt;udpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="22434-102">&lt;udpBinding&gt;</span></span>
<span data-ttu-id="22434-103">Element konfiguracji używane do konfigurowania <xref:System.ServiceModel.UdpBinding> powiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-103">A configuration element used to configure the <xref:System.ServiceModel.UdpBinding> binding.</span></span>  
  
 <span data-ttu-id="22434-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="22434-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="22434-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="22434-105">\<bindings></span></span>  
<span data-ttu-id="22434-106">\<udpBinding ></span><span class="sxs-lookup"><span data-stu-id="22434-106">\<udpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22434-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="22434-107">Syntax</span></span>  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22434-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22434-108">Attributes and Elements</span></span>  
 <span data-ttu-id="22434-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="22434-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22434-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22434-110">Attributes</span></span>  
  
|<span data-ttu-id="22434-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="22434-111">Attribute</span></span>|<span data-ttu-id="22434-112">Opis</span><span class="sxs-lookup"><span data-stu-id="22434-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="22434-113">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="22434-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="22434-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22434-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22434-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="22434-115">The default is 00:01:00.</span></span>|  
|`duplicateMessageHistoryLength`|<span data-ttu-id="22434-116">Wartość całkowita określająca długość historii zduplikowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="22434-116">An integer value that specifies the duplicate message history length.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="22434-117">Wartość całkowita określająca maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="22434-117">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="22434-118">Wartość domyślna to 524288 (0x80000) bajtów.</span><span class="sxs-lookup"><span data-stu-id="22434-118">The default value is 524288 (0x80000) bytes.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="22434-119">Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania dla punkt końcowy skonfigurowany dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-119">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="22434-120">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="22434-120">The default value is 65,536 bytes.</span></span>|  
|`maxPendingMessagesTotalSize`|<span data-ttu-id="22434-121">Wartość całkowita określająca maksymalną liczbę komunikatów odebranych, ale jeszcze nie są usuwane z kolejki wejściowej dla wystąpienia kanałów.</span><span class="sxs-lookup"><span data-stu-id="22434-121">An integer value that specifies the maximum number of messages that are received but not yet removed from the input queue for an individual channel instance.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="22434-122">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-122">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="22434-123">Nadawca otrzymuje błędu protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="22434-123">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="22434-124">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="22434-124">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="22434-125">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="22434-125">The default is 65,536 bytes.</span></span>|  
|`maxRetransmitCount`|<span data-ttu-id="22434-126">Wartość całkowita określająca maksymalną liczbę retransmisji komunikatów.</span><span class="sxs-lookup"><span data-stu-id="22434-126">An integer value that specifies the maximum number of retransmit messages.</span></span>|  
|`multicastInterfaceId`|<span data-ttu-id="22434-127">Wartość całkowita określająca identyfikator interfejsu multiemisji.</span><span class="sxs-lookup"><span data-stu-id="22434-127">An integer value that specifies the multicast interface ID.</span></span>|  
|`name`|<span data-ttu-id="22434-128">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="22434-129">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="22434-130">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="22434-130">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="22434-131">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="22434-131">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="22434-132">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="22434-132">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="22434-133">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="22434-133">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="22434-134">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="22434-134">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="22434-135">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22434-135">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22434-136">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="22434-136">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="22434-137">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="22434-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="22434-138">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22434-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22434-139">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="22434-139">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="22434-140">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="22434-140">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="22434-141">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="22434-141">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="22434-142">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="22434-142">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="22434-143">Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="22434-143">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="22434-144">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="22434-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22434-145">-BigEndianUnicode: Unicode BigEndian kodowanie.</span><span class="sxs-lookup"><span data-stu-id="22434-145">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="22434-146">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="22434-146">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="22434-147">-UTF8: 8-bitowego kodowania o</span><span class="sxs-lookup"><span data-stu-id="22434-147">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="22434-148">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="22434-148">The default is UTF8.</span></span> <span data-ttu-id="22434-149">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="22434-149">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`timeToLive`|<span data-ttu-id="22434-150">Wartość timespan określający czas wygaśnięcia dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-150">A timespan value that specifies the time to live for the binding.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22434-151">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22434-151">Child Elements</span></span>  
  
|<span data-ttu-id="22434-152">Element</span><span class="sxs-lookup"><span data-stu-id="22434-152">Element</span></span>|<span data-ttu-id="22434-153">Opis</span><span class="sxs-lookup"><span data-stu-id="22434-153">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22434-154">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="22434-154">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="22434-155">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="22434-155">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="22434-156">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="22434-156">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22434-157">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22434-157">Parent Elements</span></span>  
  
|<span data-ttu-id="22434-158">Element</span><span class="sxs-lookup"><span data-stu-id="22434-158">Element</span></span>|<span data-ttu-id="22434-159">Opis</span><span class="sxs-lookup"><span data-stu-id="22434-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22434-160">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="22434-160">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="22434-161">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="22434-161">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22434-162">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22434-162">Remarks</span></span>  
 <span data-ttu-id="22434-163">UdpBinding umożliwia usługi WCF do komunikowania się za pomocą transportu UDP.</span><span class="sxs-lookup"><span data-stu-id="22434-163">The UdpBinding allows WCF services to communicate over the UDP transport.</span></span> <span data-ttu-id="22434-164">Umożliwia ona "wyzwalać i zapomnij" wymiany komunikatów, gdy klient wysyła komunikat do usługi i oczekuje wstecz Brak odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="22434-164">It allows for "fire and forget" message exchanges where a client sends a message to a service and expects no response back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22434-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="22434-165">Example</span></span>  
 <span data-ttu-id="22434-166">Poniższy przykład przedstawia sposób konfigurowania <xref:System.ServiceModel.UdpBinding> przy użyciu <`udpBinding`> elementu.</span><span class="sxs-lookup"><span data-stu-id="22434-166">The following example shows how to configure the <xref:System.ServiceModel.UdpBinding> using the <`udpBinding`> element.</span></span>  
  
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
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="22434-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22434-167">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="22434-168">Powiązania</span><span class="sxs-lookup"><span data-stu-id="22434-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="22434-169">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="22434-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="22434-170">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="22434-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="22434-171">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="22434-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
