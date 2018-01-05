---
title: '&lt;udpTransportSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88b38fc7c67c404446000ca79d2c6191bfc7eed5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltudptransportsettingsgt"></a><span data-ttu-id="efc9b-102">&lt;udpTransportSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="efc9b-102">&lt;udpTransportSettings&gt;</span></span>
<span data-ttu-id="efc9b-103">Ten element konfiguracji udostępnia ustawienia transportu UDP [ \<udpDiscoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span><span class="sxs-lookup"><span data-stu-id="efc9b-103">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md).</span></span>  
  
<span data-ttu-id="efc9b-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="efc9b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="efc9b-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="efc9b-105">\<standardEndpoints></span></span>  
<span data-ttu-id="efc9b-106">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="efc9b-106">\<udpDiscoveryEndpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc9b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="efc9b-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer" 
                              maxBufferPoolSize="Integer" 
                              maxMulticastRetransmitCount="Integer" 
                              maxPendingMessageCount="Integer" 
                              maxReceivedMessageSize="Integer" 
                              maxUnicastRetransmitCount="Integer" 
                              multicastInterfaceId="String" 
                              socketReceiveBufferSize="Integer" 
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efc9b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="efc9b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="efc9b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="efc9b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efc9b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="efc9b-110">Attributes</span></span>  
  
|<span data-ttu-id="efc9b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="efc9b-111">Attribute</span></span>|<span data-ttu-id="efc9b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="efc9b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efc9b-113">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="efc9b-113">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="efc9b-114">Liczba całkowita określająca maksymalną liczbę wartości skrótu wiadomości w celu zidentyfikowania zduplikowanych komunikatów używany przez transport.</span><span class="sxs-lookup"><span data-stu-id="efc9b-114">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="efc9b-115">Wykrywanie duplikatów zostaną wykonane na poziomie Obiekt TransportManager.</span><span class="sxs-lookup"><span data-stu-id="efc9b-115">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="efc9b-116">Ustawienie tej właściwości na wartość 0 powoduje wyłączenie wykrywania duplikatów.</span><span class="sxs-lookup"><span data-stu-id="efc9b-116">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="efc9b-117">Ten atrybut umożliwia administratorom systemu lub deweloperom wyłączyć algorytmy wykrywania zduplikowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="efc9b-117">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="efc9b-118">Może to być pożądane, aby wdrożyć własny algorytm wykrywania duplikatów.</span><span class="sxs-lookup"><span data-stu-id="efc9b-118">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="efc9b-119">Wartość domyślna to 4112.</span><span class="sxs-lookup"><span data-stu-id="efc9b-119">The default is 4112.</span></span>|  
|<span data-ttu-id="efc9b-120">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="efc9b-120">maxBufferPoolSize</span></span>|<span data-ttu-id="efc9b-121">Liczba całkowita określająca maksymalny rozmiar pulami buforu, używany przez transport.</span><span class="sxs-lookup"><span data-stu-id="efc9b-121">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="efc9b-122">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="efc9b-122">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="efc9b-123">Liczba całkowita określająca maksymalną liczbę razy (oprócz pierwszego wysyłania) powinny zostać ponownie wysłane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="efc9b-123">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="efc9b-124">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="efc9b-124">The default is 2.</span></span>|  
|<span data-ttu-id="efc9b-125">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="efc9b-125">maxPendingMessageCount</span></span>|<span data-ttu-id="efc9b-126">Liczba całkowita określająca maksymalną liczbę wiadomości, które zostały odebrane, ale jeszcze nie zostały usunięte z obiektu InputQueue dla wystąpienia kanałów.</span><span class="sxs-lookup"><span data-stu-id="efc9b-126">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="efc9b-127">Jeśli obiektu InputQueue osiągnęła swój limit liczby oczekujących komunikatów, komunikat zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="efc9b-127">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="efc9b-128">Wartość domyślna to 32.</span><span class="sxs-lookup"><span data-stu-id="efc9b-128">The default is 32.</span></span>|  
|<span data-ttu-id="efc9b-129">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="efc9b-129">maxReceivedMessageSize</span></span>|<span data-ttu-id="efc9b-130">Liczba całkowita określająca maksymalny rozmiar komunikatu, który może przetworzyć wiązanie.</span><span class="sxs-lookup"><span data-stu-id="efc9b-130">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="efc9b-131">Wartość domyślna to 65507.</span><span class="sxs-lookup"><span data-stu-id="efc9b-131">The default value is 65507.</span></span>|  
|<span data-ttu-id="efc9b-132">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="efc9b-132">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="efc9b-133">Liczba całkowita określająca maksymalną liczbę razy (oprócz pierwszego wysyłania) powinny zostać ponownie wysłane wiadomości.</span><span class="sxs-lookup"><span data-stu-id="efc9b-133">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="efc9b-134">Jeśli komunikat jest wysyłany do adresu emisji pojedynczej, odebrano komunikat odpowiedzi odpowiedniego nagłówka RelatesTo retransmisji może zakończyć się wcześniej (przed zainicjowaniu o skonfigurowaną liczbę razy).</span><span class="sxs-lookup"><span data-stu-id="efc9b-134">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="efc9b-135">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="efc9b-135">The default value is 1.</span></span>|  
|<span data-ttu-id="efc9b-136">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="efc9b-136">multicastInterfaceId</span></span>|<span data-ttu-id="efc9b-137">Ciąg unikatowo identyfikujący karty sieciowej, które mają być używane podczas wysyłania i odbierania multiemisji na maszynach wieloadresowych.</span><span class="sxs-lookup"><span data-stu-id="efc9b-137">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="efc9b-138">W czasie wykonywania, transport użyje ta wartość atrybutu do wyszukiwania indeksu interfejsu, który jest następnie używana do ustawiania `IP_MULTICAST_IF` i `IPV6_MULTICAST_IF` gniazda opcje.</span><span class="sxs-lookup"><span data-stu-id="efc9b-138">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="efc9b-139">Ten sam indeks interfejsu będą używane podczas dołączanie do grupy multiemisji, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="efc9b-139">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="efc9b-140">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="efc9b-140">The default value is `null`.</span></span>|  
|<span data-ttu-id="efc9b-141">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="efc9b-141">socketReceiveBufferSize</span></span>|<span data-ttu-id="efc9b-142">Liczba całkowita określająca rozmiar buforów odbioru na podstawowym gniazda interfejsu WinSock.</span><span class="sxs-lookup"><span data-stu-id="efc9b-142">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="efc9b-143">Użytkownik odbierający kanału można użyć tego atrybutu w powiązaniu do kontroli zachowania systemu odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="efc9b-143">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="efc9b-144">Na przykład mając aplikacji, która zajmuje przychodzących komunikatów usługi WCF na maksymalną wartość progową, za pomocą większej wartości tego atrybutu umożliwia komunikaty, aby zająć w buforze WinSock podczas oczekiwania na aplikacji można było je przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="efc9b-144">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="efc9b-145">Przy użyciu niższą wartość w tej samej sytuacji spowoduje wiadomości porzucane. Ten atrybut przedstawia podstawowy WinSock `SO_RCVBUF` gniazda opcji. Wartość tego atrybutu musi być co najmniej rozmiar `maxReceivedMessageSize`.</span><span class="sxs-lookup"><span data-stu-id="efc9b-145">Using a lower value in the same situation would result in messages getting dropped.This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="efc9b-146">Ustawienie jej na wartość mniejszą niż `maxReceivedMessageSize` spowodują wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="efc9b-146">Setting it to a value smaller than the `maxReceivedMessageSize` will result in runtime exception.</span></span><br /><br /> <span data-ttu-id="efc9b-147">Wartość domyślna to 65536.</span><span class="sxs-lookup"><span data-stu-id="efc9b-147">The default value is 65536.</span></span>|  
|<span data-ttu-id="efc9b-148">Wartość TimeToLive</span><span class="sxs-lookup"><span data-stu-id="efc9b-148">timeToLive</span></span>|<span data-ttu-id="efc9b-149">Liczba całkowita określająca liczbę przeskoków sieciowych segmentu, przechodzących pakiety multiemisji.</span><span class="sxs-lookup"><span data-stu-id="efc9b-149">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="efc9b-150">Ten atrybut dostęp do funkcji skojarzonych z `IP_MULTICAST_TTL` i `IP_TTL` gniazda opcje.</span><span class="sxs-lookup"><span data-stu-id="efc9b-150">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="efc9b-151">Wartość domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="efc9b-151">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efc9b-152">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="efc9b-152">Child Elements</span></span>  
 <span data-ttu-id="efc9b-153">Brak.</span><span class="sxs-lookup"><span data-stu-id="efc9b-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efc9b-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="efc9b-154">Parent Elements</span></span>  
  
|<span data-ttu-id="efc9b-155">Element</span><span class="sxs-lookup"><span data-stu-id="efc9b-155">Element</span></span>|<span data-ttu-id="efc9b-156">Opis</span><span class="sxs-lookup"><span data-stu-id="efc9b-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efc9b-157">\<udpDiscoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="efc9b-157">\<udpDiscoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|<span data-ttu-id="efc9b-158">Standardowy punkt końcowy ze stałym odnajdywania powiązania transportu kontraktu i UDP.</span><span class="sxs-lookup"><span data-stu-id="efc9b-158">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efc9b-159">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efc9b-159">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.UdpTransportSettings>
