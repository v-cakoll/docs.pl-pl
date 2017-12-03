---
title: '&lt;connectionPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f1980365da8514060290066a4e15e5f88e35f7f4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltconnectionpoolsettingsgt"></a><span data-ttu-id="94362-102">&lt;connectionPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="94362-102">&lt;connectionPoolSettings&gt;</span></span>
<span data-ttu-id="94362-103">Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="94362-103">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
 <span data-ttu-id="94362-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="94362-104">\<system.serviceModel></span></span>  
<span data-ttu-id="94362-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="94362-105">\<bindings></span></span>  
<span data-ttu-id="94362-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="94362-106">\<customBinding></span></span>  
<span data-ttu-id="94362-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="94362-107">\<binding></span></span>  
<span data-ttu-id="94362-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="94362-108">\<namePipeTransport></span></span>  
<span data-ttu-id="94362-109">\<connectionPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="94362-109">\<connectionPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94362-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="94362-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings  
        groupName="String"  
    idleTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94362-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="94362-111">Attributes and Elements</span></span>  
 <span data-ttu-id="94362-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="94362-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94362-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="94362-113">Attributes</span></span>  
  
|<span data-ttu-id="94362-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="94362-114">Attribute</span></span>|<span data-ttu-id="94362-115">Opis</span><span class="sxs-lookup"><span data-stu-id="94362-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="94362-116">Ciąg, który definiuje nazwę puli połączeń dla wychodzących kanałów.</span><span class="sxs-lookup"><span data-stu-id="94362-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="94362-117">W trybie przesyłanej strumieniowo połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="94362-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="94362-118">Wartość domyślna to ciąg "domyślny".</span><span class="sxs-lookup"><span data-stu-id="94362-118">The default is a "default" string.</span></span> <span data-ttu-id="94362-119">Można zmodyfikować tę wartość, aby odizolować połączeń dla określonego klienta do oddzielnych grup.</span><span class="sxs-lookup"><span data-stu-id="94362-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="94362-120">Dodatnią <xref:System.TimeSpan> , który określa maksymalny czas, połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="94362-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="94362-121">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="94362-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="94362-122">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń do zdalnego punktu końcowego, inicjowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="94362-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="94362-123">Połączenia poza limitem są umieszczane w kolejce, dopóki nie będzie dostępne miejsce poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="94362-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="94362-124">`idleTimeout` Ogranicza okres, w którym połączenia pozostają w kolejce przed jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="94362-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="94362-125">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="94362-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="94362-126">Ten atrybut ogranicza liczbę równoczesnych aktywnych połączeń z klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94362-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="94362-127">Tę wartość po przekroczeniu dzięki użyciu aktywnych połączeń klienckich, usługi mogą być wyświetlane odpowiadać do klienta.</span><span class="sxs-lookup"><span data-stu-id="94362-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="94362-128">W takim przypadku ta wartość powinna dostosowana do przekracza maksymalną liczbę oczekiwanych równoczesnych połączeń klientów do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="94362-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94362-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="94362-129">Child Elements</span></span>  
 <span data-ttu-id="94362-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="94362-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94362-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="94362-131">Parent Elements</span></span>  
  
|<span data-ttu-id="94362-132">Element</span><span class="sxs-lookup"><span data-stu-id="94362-132">Element</span></span>|<span data-ttu-id="94362-133">Opis</span><span class="sxs-lookup"><span data-stu-id="94362-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94362-134">\<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="94362-134">\<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/namedpipetransport.md)|<span data-ttu-id="94362-135">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="94362-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94362-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="94362-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="94362-137">Transporty</span><span class="sxs-lookup"><span data-stu-id="94362-137">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="94362-138">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="94362-138">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="94362-139">Powiązania</span><span class="sxs-lookup"><span data-stu-id="94362-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="94362-140">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="94362-140">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="94362-141">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="94362-141">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="94362-142">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="94362-142">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
