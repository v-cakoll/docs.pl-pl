---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: d896953a7ed31fdaf5f357a8721c7d085d50bc56
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400052"
---
# <a name="peertransport"></a><span data-ttu-id="719c7-101">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="719c7-101">\<peerTransport></span></span>
<span data-ttu-id="719c7-102">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="719c7-102">Defines a peer transport for a custom binding.</span></span>  
  
<span data-ttu-id="719c7-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="719c7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="719c7-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="719c7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="719c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="719c7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="719c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="719c7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="719c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="719c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="719c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerTransport >**</span><span class="sxs-lookup"><span data-stu-id="719c7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="719c7-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="719c7-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="719c7-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="719c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="719c7-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="719c7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="719c7-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="719c7-112">Attributes</span></span>  
  
|<span data-ttu-id="719c7-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="719c7-113">Attribute</span></span>|<span data-ttu-id="719c7-114">Opis</span><span class="sxs-lookup"><span data-stu-id="719c7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="719c7-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="719c7-115">listenIpAddress</span></span>|<span data-ttu-id="719c7-116">Ciąg określający adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="719c7-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="719c7-117">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="719c7-117">The default is `null`.</span></span>|  
|<span data-ttu-id="719c7-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="719c7-118">maxBufferPoolSize</span></span>|<span data-ttu-id="719c7-119">Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów.</span><span class="sxs-lookup"><span data-stu-id="719c7-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="719c7-120">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="719c7-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="719c7-121">Wiele części usługi WCF korzysta z buforów.</span><span class="sxs-lookup"><span data-stu-id="719c7-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="719c7-122">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="719c7-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="719c7-123">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="719c7-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="719c7-124">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="719c7-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="719c7-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="719c7-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="719c7-126">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami.</span><span class="sxs-lookup"><span data-stu-id="719c7-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="719c7-127">Nadawca komunikatu otrzymuje błąd protokołu SOAP, gdy komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="719c7-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="719c7-128">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="719c7-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="719c7-129">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="719c7-129">The default is 65536.</span></span>|  
|<span data-ttu-id="719c7-130">port</span><span class="sxs-lookup"><span data-stu-id="719c7-130">port</span></span>|<span data-ttu-id="719c7-131">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzać komunikaty protokołu TCP kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="719c7-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="719c7-132">Ta wartość musi należeć <xref:System.Net.IPEndPoint.MinPort> do <xref:System.Net.IPEndPoint.MaxPort>zakresu od do.</span><span class="sxs-lookup"><span data-stu-id="719c7-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="719c7-133">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="719c7-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="719c7-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="719c7-134">Child Elements</span></span>  
  
|<span data-ttu-id="719c7-135">Element</span><span class="sxs-lookup"><span data-stu-id="719c7-135">Element</span></span>|<span data-ttu-id="719c7-136">Opis</span><span class="sxs-lookup"><span data-stu-id="719c7-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="719c7-137">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="719c7-137">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="719c7-138">Definiuje ustawienia zabezpieczeń dla tego transportu.</span><span class="sxs-lookup"><span data-stu-id="719c7-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="719c7-139">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="719c7-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="719c7-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="719c7-140">Parent Elements</span></span>  
  
|<span data-ttu-id="719c7-141">Element</span><span class="sxs-lookup"><span data-stu-id="719c7-141">Element</span></span>|<span data-ttu-id="719c7-142">Opis</span><span class="sxs-lookup"><span data-stu-id="719c7-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="719c7-143">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="719c7-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="719c7-144">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="719c7-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="719c7-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="719c7-145">Remarks</span></span>  
 <span data-ttu-id="719c7-146">Nie można używać tego transportu z kontraktami, które mają operacje żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="719c7-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="719c7-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="719c7-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="719c7-148">Transporty</span><span class="sxs-lookup"><span data-stu-id="719c7-148">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="719c7-149">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="719c7-149">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="719c7-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="719c7-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="719c7-151">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="719c7-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="719c7-152">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="719c7-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="719c7-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="719c7-153">\<customBinding></span></span>](custombinding.md)
