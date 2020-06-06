---
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: 99fb013e052329ae4b99c4db89565ace8935c456
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736506"
---
# \<peerTransport>
<span data-ttu-id="6a5d9-101">Definiuje transport równorzędny dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-101">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="6a5d9-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a5d9-102">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a5d9-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6a5d9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6a5d9-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a5d9-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6a5d9-105">Attributes</span></span>  
  
|<span data-ttu-id="6a5d9-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6a5d9-106">Attribute</span></span>|<span data-ttu-id="6a5d9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6a5d9-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6a5d9-108">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="6a5d9-108">listenIpAddress</span></span>|<span data-ttu-id="6a5d9-109">Ciąg określający adres IP, na którym węzeł równorzędny będzie nasłuchiwać komunikatów TCP.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-109">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="6a5d9-110">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-110">The default is `null`.</span></span>|  
|<span data-ttu-id="6a5d9-111">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="6a5d9-111">maxBufferPoolSize</span></span>|<span data-ttu-id="6a5d9-112">Dodatnia liczba całkowita, która określa maksymalny rozmiar puli buforów.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-112">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="6a5d9-113">Wartość domyślna to 524288.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-113">The default is 524288.</span></span><br /><br /> <span data-ttu-id="6a5d9-114">Wiele części usługi WCF korzysta z buforów.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-114">Many parts of WCF use buffers.</span></span> <span data-ttu-id="6a5d9-115">Tworzenie i niszczenie buforów za każdym razem, gdy są używane, jest kosztowne i wyrzucanie elementów bezużytecznych dla buforów jest również kosztowne.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-115">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="6a5d9-116">W przypadku pul buforów można pobrać bufor z puli, użyć go i zwrócić do puli po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-116">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="6a5d9-117">W ten sposób nie ma konieczności narzutu na tworzenie i niszczenie buforów.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-117">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="6a5d9-118">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="6a5d9-118">maxReceivedMessageSize</span></span>|<span data-ttu-id="6a5d9-119">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości w bajtach, włącznie z nagłówkami.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-119">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="6a5d9-120">Nadawca komunikatu otrzymuje błąd protokołu SOAP, gdy komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-120">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="6a5d9-121">Odbiorca odrzuca komunikat i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-121">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="6a5d9-122">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-122">The default is 65536.</span></span>|  
|<span data-ttu-id="6a5d9-123">port</span><span class="sxs-lookup"><span data-stu-id="6a5d9-123">port</span></span>|<span data-ttu-id="6a5d9-124">Liczba całkowita określająca port interfejsu sieciowego, na którym to powiązanie będzie przetwarzać komunikaty protokołu TCP kanału równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-124">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="6a5d9-125">Ta wartość musi należeć <xref:System.Net.IPEndPoint.MinPort> do zakresu od do <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="6a5d9-125">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="6a5d9-126">Wartość domyślna to 0.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-126">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a5d9-127">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6a5d9-127">Child Elements</span></span>  
  
|<span data-ttu-id="6a5d9-128">Element</span><span class="sxs-lookup"><span data-stu-id="6a5d9-128">Element</span></span>|<span data-ttu-id="6a5d9-129">Opis</span><span class="sxs-lookup"><span data-stu-id="6a5d9-129">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="6a5d9-130">Definiuje ustawienia zabezpieczeń dla tego transportu.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-130">Defines the security settings for this transport.</span></span> <span data-ttu-id="6a5d9-131">Ten element jest typu <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="6a5d9-131">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6a5d9-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6a5d9-132">Parent Elements</span></span>  
  
|<span data-ttu-id="6a5d9-133">Element</span><span class="sxs-lookup"><span data-stu-id="6a5d9-133">Element</span></span>|<span data-ttu-id="6a5d9-134">Opis</span><span class="sxs-lookup"><span data-stu-id="6a5d9-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="6a5d9-135">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-135">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a5d9-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a5d9-136">Remarks</span></span>  
 <span data-ttu-id="6a5d9-137">Nie można używać tego transportu z kontraktami, które mają operacje żądania/odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="6a5d9-137">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5d9-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a5d9-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6a5d9-139">Transporty</span><span class="sxs-lookup"><span data-stu-id="6a5d9-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="6a5d9-140">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="6a5d9-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="6a5d9-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6a5d9-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6a5d9-142">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="6a5d9-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6a5d9-143">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6a5d9-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
