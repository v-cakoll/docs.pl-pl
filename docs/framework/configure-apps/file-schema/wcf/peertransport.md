---
title: '&lt;peerTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfa8c480524c920ac2f73236b6548072e7805ab2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeertransportgt"></a><span data-ttu-id="ef27b-102">&lt;peerTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="ef27b-102">&lt;peerTransport&gt;</span></span>
<span data-ttu-id="ef27b-103">Definiuje transport elementu równorzędnego dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ef27b-103">Defines a peer transport for a custom binding.</span></span>  
  
 <span data-ttu-id="ef27b-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="ef27b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ef27b-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ef27b-105">\<bindings></span></span>  
<span data-ttu-id="ef27b-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ef27b-106">\<customBinding></span></span>  
<span data-ttu-id="ef27b-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ef27b-107">\<binding></span></span>  
<span data-ttu-id="ef27b-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="ef27b-108">\<peerTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef27b-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef27b-109">Syntax</span></span>  
  
```xml  
<peerTransport   
    listenIpAddress="String"  
    maxBufferPoolSize="Integer"  
    maxReceivedMessageSize="Integer"  
    port="Integer"  
        <security>  
    </security>  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef27b-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ef27b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ef27b-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ef27b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef27b-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ef27b-112">Attributes</span></span>  
  
|<span data-ttu-id="ef27b-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ef27b-113">Attribute</span></span>|<span data-ttu-id="ef27b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ef27b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef27b-115">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="ef27b-115">listenIpAddress</span></span>|<span data-ttu-id="ef27b-116">Ciąg, który określa adres IP, na którym węzeł elementu równorzędnego będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="ef27b-116">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="ef27b-117">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="ef27b-117">The default is `null`.</span></span>|  
|<span data-ttu-id="ef27b-118">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="ef27b-118">maxBufferPoolSize</span></span>|<span data-ttu-id="ef27b-119">Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów.</span><span class="sxs-lookup"><span data-stu-id="ef27b-119">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="ef27b-120">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="ef27b-120">The default is 524288.</span></span><br /><br /> <span data-ttu-id="ef27b-121">Wiele elementów WCF za pomocą buforów.</span><span class="sxs-lookup"><span data-stu-id="ef27b-121">Many parts of WCF use buffers.</span></span> <span data-ttu-id="ef27b-122">Tworzenie i niszczenie buforów za każdym razem, gdy są one używane jest kosztowne i odzyskiwanie pamięci dla buforów również jest kosztowna.</span><span class="sxs-lookup"><span data-stu-id="ef27b-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="ef27b-123">Używając puli buforów można podjąć buforu z puli, ten jest używany i zwracać do puli, gdy wszystko będzie gotowe.</span><span class="sxs-lookup"><span data-stu-id="ef27b-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="ef27b-124">W związku z tym jest unikać obciążenie związane z tworzeniem i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="ef27b-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="ef27b-125">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="ef27b-125">maxReceivedMessageSize</span></span>|<span data-ttu-id="ef27b-126">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami.</span><span class="sxs-lookup"><span data-stu-id="ef27b-126">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="ef27b-127">Nadawca komunikatu otrzymuje błędu protokołu SOAP wiadomości jest za duża dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="ef27b-127">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="ef27b-128">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="ef27b-128">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="ef27b-129">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="ef27b-129">The default is 65536.</span></span>|  
|<span data-ttu-id="ef27b-130">port</span><span class="sxs-lookup"><span data-stu-id="ef27b-130">port</span></span>|<span data-ttu-id="ef27b-131">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzało równorzędny kanał komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="ef27b-131">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="ef27b-132">Ta wartość musi należeć do zakresu od <xref:System.Net.IPEndPoint.MinPort> i <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="ef27b-132">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="ef27b-133">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="ef27b-133">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef27b-134">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ef27b-134">Child Elements</span></span>  
  
|<span data-ttu-id="ef27b-135">Element</span><span class="sxs-lookup"><span data-stu-id="ef27b-135">Element</span></span>|<span data-ttu-id="ef27b-136">Opis</span><span class="sxs-lookup"><span data-stu-id="ef27b-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef27b-137">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="ef27b-137">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="ef27b-138">Definiuje ustawienia zabezpieczeń dla tego transportu.</span><span class="sxs-lookup"><span data-stu-id="ef27b-138">Defines the security settings for this transport.</span></span> <span data-ttu-id="ef27b-139">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ef27b-139">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef27b-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ef27b-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ef27b-141">Element</span><span class="sxs-lookup"><span data-stu-id="ef27b-141">Element</span></span>|<span data-ttu-id="ef27b-142">Opis</span><span class="sxs-lookup"><span data-stu-id="ef27b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef27b-143">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ef27b-143">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ef27b-144">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ef27b-144">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef27b-145">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef27b-145">Remarks</span></span>  
 <span data-ttu-id="ef27b-146">Nie można używać tego transportu z kontraktów żądania/odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="ef27b-146">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef27b-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef27b-147">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportElement>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="ef27b-148">Transporty</span><span class="sxs-lookup"><span data-stu-id="ef27b-148">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="ef27b-149">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="ef27b-149">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="ef27b-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ef27b-150">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ef27b-151">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="ef27b-151">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="ef27b-152">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ef27b-152">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="ef27b-153">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ef27b-153">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
