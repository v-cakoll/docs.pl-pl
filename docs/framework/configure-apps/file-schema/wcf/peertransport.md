---
title: '&lt;peerTransport&gt;'
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: c8ca9f37b799087337f7dff6be48744f4f9dea6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703630"
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="903ad-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="903ad-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="903ad-103">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="903ad-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="903ad-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="903ad-104">\<system.serviceModel></span></span>  
<span data-ttu-id="903ad-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="903ad-105">\<bindings></span></span>  
<span data-ttu-id="903ad-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="903ad-106">\<customBinding></span></span>  
<span data-ttu-id="903ad-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="903ad-107">\<binding></span></span>  
<span data-ttu-id="903ad-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="903ad-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="903ad-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="903ad-109">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="903ad-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="903ad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="903ad-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="903ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="903ad-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="903ad-112">Attributes</span></span>  
  
|<span data-ttu-id="903ad-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="903ad-113">Attribute</span></span>|<span data-ttu-id="903ad-114">Opis</span><span class="sxs-lookup"><span data-stu-id="903ad-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="903ad-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="903ad-115">listenIpAddress</span></span>|<span data-ttu-id="903ad-116">Ciąg, który określa adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="903ad-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="903ad-117">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="903ad-117">The default is `null`.</span></span>|  
|<span data-ttu-id="903ad-118">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="903ad-118">maxBufferPoolSize</span></span>|<span data-ttu-id="903ad-119">Dodatnia liczba całkowita, która określa maksymalny rozmiar puli bufora.</span><span class="sxs-lookup"><span data-stu-id="903ad-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="903ad-120">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="903ad-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="903ad-121">Wiele elementów usług WCF za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="903ad-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="903ad-122">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="903ad-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="903ad-123">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="903ad-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="903ad-124">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="903ad-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="903ad-125">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="903ad-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="903ad-126">Dodatnia liczba całkowita określająca maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami.</span><span class="sxs-lookup"><span data-stu-id="903ad-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="903ad-127">Nadawca wiadomości otrzymuje protokołu SOAP wiadomości jest za duża dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="903ad-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="903ad-128">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="903ad-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="903ad-129">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="903ad-129">The default is 65536.</span></span>|  
|<span data-ttu-id="903ad-130">port</span><span class="sxs-lookup"><span data-stu-id="903ad-130">port</span></span>|<span data-ttu-id="903ad-131">Liczba całkowita określająca port interfejsu sieciowego, w którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="903ad-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="903ad-132">Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="903ad-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="903ad-133">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="903ad-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="903ad-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="903ad-134">Child Elements</span></span>  
  
|<span data-ttu-id="903ad-135">Element</span><span class="sxs-lookup"><span data-stu-id="903ad-135">Element</span></span>|<span data-ttu-id="903ad-136">Opis</span><span class="sxs-lookup"><span data-stu-id="903ad-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="903ad-137">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="903ad-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="903ad-138">Definiuje ustawienia zabezpieczeń dla tego transportu.</span><span class="sxs-lookup"><span data-stu-id="903ad-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="903ad-139">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="903ad-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="903ad-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="903ad-140">Parent Elements</span></span>  
  
|<span data-ttu-id="903ad-141">Element</span><span class="sxs-lookup"><span data-stu-id="903ad-141">Element</span></span>|<span data-ttu-id="903ad-142">Opis</span><span class="sxs-lookup"><span data-stu-id="903ad-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="903ad-143">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="903ad-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="903ad-144">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="903ad-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="903ad-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="903ad-145">Remarks</span></span>  
 <span data-ttu-id="903ad-146">Nie można użyć tego transportu za pomocą kontraktów typu żądanie/odpowiedź operacji.</span><span class="sxs-lookup"><span data-stu-id="903ad-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="903ad-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="903ad-147">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="903ad-148">Transporty</span><span class="sxs-lookup"><span data-stu-id="903ad-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="903ad-149">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="903ad-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="903ad-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="903ad-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="903ad-151">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="903ad-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="903ad-152">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="903ad-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="903ad-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="903ad-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
