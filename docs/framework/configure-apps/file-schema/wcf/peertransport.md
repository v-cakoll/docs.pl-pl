---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 8962a0c018442ed590b62e53ea8323d80e334df7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290098"
---
# <a name="peertransport"></a><span data-ttu-id="f3291-101">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="f3291-101">\<peerTransport></span></span>
<span data-ttu-id="f3291-102">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f3291-102">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="f3291-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f3291-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f3291-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="f3291-104">\<bindings></span></span>  
<span data-ttu-id="f3291-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f3291-105">\<customBinding></span></span>  
<span data-ttu-id="f3291-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f3291-106">\<binding></span></span>  
<span data-ttu-id="f3291-107">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="f3291-107">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3291-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3291-108">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3291-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3291-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3291-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3291-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3291-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3291-111">Attributes</span></span>  
  
|<span data-ttu-id="f3291-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f3291-112">Attribute</span></span>|<span data-ttu-id="f3291-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f3291-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3291-114">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="f3291-114">listenIpAddress</span></span>|<span data-ttu-id="f3291-115">Ciąg, który określa adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="f3291-115">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="f3291-116">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="f3291-116">The default is `null`.</span></span>|  
|<span data-ttu-id="f3291-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f3291-117">maxBufferPoolSize</span></span>|<span data-ttu-id="f3291-118">Dodatnia liczba całkowita, która określa maksymalny rozmiar puli bufora.</span><span class="sxs-lookup"><span data-stu-id="f3291-118">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="f3291-119">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="f3291-119">The default is 524288.</span></span><br /><br /> <span data-ttu-id="f3291-120">Wiele elementów usług WCF za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="f3291-120">Many parts of WCF use buffers.</span></span> <span data-ttu-id="f3291-121">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne, a także jest kosztowne wyrzucania elementów bezużytecznych dla buforów.</span><span class="sxs-lookup"><span data-stu-id="f3291-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f3291-122">Dzięki pulom buforu zająć buforu z puli, go używać i przywrócić go do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="f3291-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f3291-123">Ten sposób unika się obciążenie tworzeniem i likwidowaniem buforów.</span><span class="sxs-lookup"><span data-stu-id="f3291-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="f3291-124">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f3291-124">maxReceivedMessageSize</span></span>|<span data-ttu-id="f3291-125">Dodatnia liczba całkowita określająca maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami.</span><span class="sxs-lookup"><span data-stu-id="f3291-125">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="f3291-126">Nadawca wiadomości otrzymuje protokołu SOAP wiadomości jest za duża dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="f3291-126">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="f3291-127">Należy określić odbiorcę porzuca wiadomość i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f3291-127">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f3291-128">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="f3291-128">The default is 65536.</span></span>|  
|<span data-ttu-id="f3291-129">port</span><span class="sxs-lookup"><span data-stu-id="f3291-129">port</span></span>|<span data-ttu-id="f3291-130">Liczba całkowita określająca port interfejsu sieciowego, w którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="f3291-130">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="f3291-131">Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="f3291-131">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="f3291-132">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="f3291-132">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3291-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3291-133">Child Elements</span></span>  
  
|<span data-ttu-id="f3291-134">Element</span><span class="sxs-lookup"><span data-stu-id="f3291-134">Element</span></span>|<span data-ttu-id="f3291-135">Opis</span><span class="sxs-lookup"><span data-stu-id="f3291-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3291-136">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="f3291-136">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="f3291-137">Definiuje ustawienia zabezpieczeń dla tego transportu.</span><span class="sxs-lookup"><span data-stu-id="f3291-137">Defines the security settings for this transport.</span></span> <span data-ttu-id="f3291-138">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f3291-138">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3291-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3291-139">Parent Elements</span></span>  
  
|<span data-ttu-id="f3291-140">Element</span><span class="sxs-lookup"><span data-stu-id="f3291-140">Element</span></span>|<span data-ttu-id="f3291-141">Opis</span><span class="sxs-lookup"><span data-stu-id="f3291-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3291-142">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="f3291-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="f3291-143">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f3291-143">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3291-144">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3291-144">Remarks</span></span>  
 <span data-ttu-id="f3291-145">Nie można użyć tego transportu za pomocą kontraktów typu żądanie/odpowiedź operacji.</span><span class="sxs-lookup"><span data-stu-id="f3291-145">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3291-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3291-146">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f3291-147">Transporty</span><span class="sxs-lookup"><span data-stu-id="f3291-147">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="f3291-148">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="f3291-148">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="f3291-149">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f3291-149">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="f3291-150">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f3291-150">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f3291-151">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f3291-151">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f3291-152">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f3291-152">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
