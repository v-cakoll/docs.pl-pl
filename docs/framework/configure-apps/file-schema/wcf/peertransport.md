---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 1ad05fd9125ecc8b3d5797e0dd335adbf808db84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933845"
---
# <a name="peertransport"></a><span data-ttu-id="5dade-101">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="5dade-101">\<peerTransport></span></span>
<span data-ttu-id="5dade-102">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5dade-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="5dade-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5dade-103">\<system.serviceModel></span></span>  
<span data-ttu-id="5dade-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="5dade-104">\<bindings></span></span>  
<span data-ttu-id="5dade-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5dade-105">\<customBinding></span></span>  
<span data-ttu-id="5dade-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="5dade-106">\<binding></span></span>  
<span data-ttu-id="5dade-107">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="5dade-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dade-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="5dade-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5dade-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5dade-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5dade-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5dade-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5dade-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5dade-111">Attributes</span></span>  
  
|<span data-ttu-id="5dade-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5dade-112">Attribute</span></span>|<span data-ttu-id="5dade-113">Opis</span><span class="sxs-lookup"><span data-stu-id="5dade-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5dade-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="5dade-114">listenIpAddress</span></span>|<span data-ttu-id="5dade-115">Ciąg określający adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="5dade-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="5dade-116">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="5dade-116">The default is `null`.</span></span>|  
|<span data-ttu-id="5dade-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="5dade-117">maxBufferPoolSize</span></span>|<span data-ttu-id="5dade-118">Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów.</span><span class="sxs-lookup"><span data-stu-id="5dade-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="5dade-119">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="5dade-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="5dade-120">Wiele części usługi WCF korzysta z buforów.</span><span class="sxs-lookup"><span data-stu-id="5dade-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="5dade-121">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="5dade-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="5dade-122">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="5dade-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="5dade-123">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="5dade-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="5dade-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="5dade-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="5dade-125">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami.</span><span class="sxs-lookup"><span data-stu-id="5dade-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="5dade-126">Nadawca komunikatu otrzymuje błąd protokołu SOAP, gdy komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="5dade-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="5dade-127">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5dade-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="5dade-128">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="5dade-128">The default is 65536.</span></span>|  
|<span data-ttu-id="5dade-129">port</span><span class="sxs-lookup"><span data-stu-id="5dade-129">port</span></span>|<span data-ttu-id="5dade-130">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzać komunikaty protokołu TCP kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="5dade-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="5dade-131">Ta wartość musi należeć <xref:System.Net.IPEndPoint.MinPort> do <xref:System.Net.IPEndPoint.MaxPort>zakresu od do.</span><span class="sxs-lookup"><span data-stu-id="5dade-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="5dade-132">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="5dade-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5dade-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5dade-133">Child Elements</span></span>  
  
|<span data-ttu-id="5dade-134">Element</span><span class="sxs-lookup"><span data-stu-id="5dade-134">Element</span></span>|<span data-ttu-id="5dade-135">Opis</span><span class="sxs-lookup"><span data-stu-id="5dade-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dade-136">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="5dade-136">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="5dade-137">Definiuje ustawienia zabezpieczeń dla tego transportu.</span><span class="sxs-lookup"><span data-stu-id="5dade-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="5dade-138">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5dade-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5dade-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5dade-139">Parent Elements</span></span>  
  
|<span data-ttu-id="5dade-140">Element</span><span class="sxs-lookup"><span data-stu-id="5dade-140">Element</span></span>|<span data-ttu-id="5dade-141">Opis</span><span class="sxs-lookup"><span data-stu-id="5dade-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5dade-142">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="5dade-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="5dade-143">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="5dade-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5dade-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5dade-144">Remarks</span></span>  
 <span data-ttu-id="5dade-145">Nie można używać tego transportu z kontraktami, które mają operacje żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="5dade-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dade-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5dade-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5dade-147">Transporty</span><span class="sxs-lookup"><span data-stu-id="5dade-147">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="5dade-148">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="5dade-148">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="5dade-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5dade-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5dade-150">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="5dade-150">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5dade-151">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="5dade-151">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5dade-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5dade-152">\<customBinding></span></span>](custombinding.md)
