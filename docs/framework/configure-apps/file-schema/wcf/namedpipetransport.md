---
title: '&lt;namedPipeTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3083fe7f8663007cfcc6e335b2dcf4c51d2ebc8a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltnamedpipetransportgt"></a><span data-ttu-id="245ef-102">&lt;namedPipeTransport&gt;</span><span class="sxs-lookup"><span data-stu-id="245ef-102">&lt;namedPipeTransport&gt;</span></span>
<span data-ttu-id="245ef-103">Definiuje transport, powodujący przesył kanałem wiadomości używając potoków nazwanych, gdy jest włączony do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="245ef-103">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
<span data-ttu-id="245ef-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="245ef-104">\<system.serviceModel></span></span>  
<span data-ttu-id="245ef-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="245ef-105">\<bindings></span></span>  
<span data-ttu-id="245ef-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="245ef-106">\<customBinding></span></span>  
<span data-ttu-id="245ef-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="245ef-107">\<binding></span></span>  
<span data-ttu-id="245ef-108">\<namePipeTransport ></span><span class="sxs-lookup"><span data-stu-id="245ef-108">\<namePipeTransport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="245ef-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="245ef-109">Syntax</span></span>  
  
```xml
<namedPipeTransport channelInitializationTimeout="TimeSpan"   
                    connectionBufferSize="Integer"   
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
                    manualAddressing="Boolean"   
                    maxBufferPoolSize="Integer"  
                    maxBufferSize="Integer"  
                    maxOutputDelay="TimeSpan"  
                    maxPendingAccepts="Integer"   
                    maxPendingConnections="Integer"  
                    maxReceivedMessageSize="Integer"   
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">  
  <connectionPoolSettings groupName="String" 
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="245ef-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="245ef-110">Attributes and Elements</span></span>  
<span data-ttu-id="245ef-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="245ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="245ef-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="245ef-112">Attributes</span></span>  
<span data-ttu-id="245ef-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="245ef-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="245ef-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="245ef-114">Child Elements</span></span>  
  
|<span data-ttu-id="245ef-115">Element</span><span class="sxs-lookup"><span data-stu-id="245ef-115">Element</span></span>|<span data-ttu-id="245ef-116">Opis</span><span class="sxs-lookup"><span data-stu-id="245ef-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="245ef-117">limitu czasu channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="245ef-117">ChannelInitializationTimeout</span></span>|<span data-ttu-id="245ef-118">Pobiera lub ustawia <xref:System.TimeSpan> , który określa maksymalny czas kanału może być w stanie inicjowania przed rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="245ef-118">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="245ef-119">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="245ef-119">ConnectionBufferSize</span></span>|<span data-ttu-id="245ef-120">Pobiera lub ustawia rozmiar buforu używany do przesyłania fragmentu szeregowanego komunikatu podczas transmisji od klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="245ef-120">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="245ef-121">parametru hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="245ef-121">hostNameComparisonMode</span></span>|<span data-ttu-id="245ef-122">Pobiera lub ustawia wartość wskazującą, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="245ef-122">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="245ef-123">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="245ef-123">manualAddressing</span></span>|<span data-ttu-id="245ef-124">Pobiera lub ustawia wartość wskazującą, czy ręcznego adresowania wiadomości jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="245ef-124">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="245ef-125">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="245ef-125">maxBufferPoolSize</span></span>|<span data-ttu-id="245ef-126">Pobiera lub ustawia maksymalny rozmiar w bajtach pulami buforu, używany przez transport.</span><span class="sxs-lookup"><span data-stu-id="245ef-126">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="245ef-127">wartość maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="245ef-127">maxBufferSize</span></span>|<span data-ttu-id="245ef-128">Pobiera lub ustawia maksymalny rozmiar buforu do użycia.</span><span class="sxs-lookup"><span data-stu-id="245ef-128">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="245ef-129">Dla strumienia wiadomości wartość ta powinna być co najmniej maksymalna liczba nagłówków komunikatów, które są odczytywane w tryb buforowany.</span><span class="sxs-lookup"><span data-stu-id="245ef-129">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="245ef-130">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="245ef-130">maxOutputDelay</span></span>|<span data-ttu-id="245ef-131">Pobiera lub ustawia maksymalny interwał czasu, przez który fragment lub całość komunikatu może pozostawać buforowane w pamięci przed wysłaniem.</span><span class="sxs-lookup"><span data-stu-id="245ef-131">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="245ef-132">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="245ef-132">maxPendingAccepts</span></span>|<span data-ttu-id="245ef-133">Pobiera lub ustawia maksymalną liczbę kanałów, usługa może mieć oczekiwanie na odbiornik na potrzeby przetwarzania przychodzących połączeń z usługą.</span><span class="sxs-lookup"><span data-stu-id="245ef-133">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="245ef-134">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="245ef-134">maxPendingConnections</span></span>|<span data-ttu-id="245ef-135">Pobiera lub ustawia maksymalną liczbę połączeń oczekujących na wysyłania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="245ef-135">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="245ef-136">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="245ef-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="245ef-137">Pobiera i ustawia maksymalny dopuszczalny rozmiar wiadomości, w bajtach, które mogą być odebrane.</span><span class="sxs-lookup"><span data-stu-id="245ef-137">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="245ef-138">Tryb transferu</span><span class="sxs-lookup"><span data-stu-id="245ef-138">transferMode</span></span>|<span data-ttu-id="245ef-139">Pobiera lub ustawia wartość wskazującą, czy komunikaty są buforowane, czy strumieniowo z nawiązaniem połączenia transportu.</span><span class="sxs-lookup"><span data-stu-id="245ef-139">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="245ef-140">\<connectionPoolSettings > z \<namedPipeTransport ></span><span class="sxs-lookup"><span data-stu-id="245ef-140">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|<span data-ttu-id="245ef-141">Określa ustawienia puli dodatkowego połączenia powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="245ef-141">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="245ef-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="245ef-142">Parent Elements</span></span>  
  
|<span data-ttu-id="245ef-143">Element</span><span class="sxs-lookup"><span data-stu-id="245ef-143">Element</span></span>|<span data-ttu-id="245ef-144">Opis</span><span class="sxs-lookup"><span data-stu-id="245ef-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="245ef-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="245ef-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="245ef-146">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="245ef-146">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="245ef-147">Uwagi</span><span class="sxs-lookup"><span data-stu-id="245ef-147">Remarks</span></span>  
<span data-ttu-id="245ef-148">Identyfikatory URI w postaci "net.pipe://hostname/path" korzysta z tego transportu.</span><span class="sxs-lookup"><span data-stu-id="245ef-148">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="245ef-149">Inne składniki identyfikatora URI są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="245ef-149">Other URI components are optional.</span></span>  
  
<span data-ttu-id="245ef-150">`namedPipeTransport` Element jest punkt początkowy do tworzenia niestandardowego powiązania, który implementuje ten protokół transportu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="245ef-150">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="245ef-151">Ten transport jest używany dla na komputerze z systemem Windows Communication Foundation (WCF) - do - komunikacyjny WCF.</span><span class="sxs-lookup"><span data-stu-id="245ef-151">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="245ef-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="245ef-152">See Also</span></span>  
<span data-ttu-id="245ef-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span><span class="sxs-lookup"><span data-stu-id="245ef-153"><xref:System.ServiceModel.Configuration.NamedPipeTransportElement></span></span>   
<span data-ttu-id="245ef-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="245ef-154"><xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement></span></span>   
<span data-ttu-id="245ef-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span><span class="sxs-lookup"><span data-stu-id="245ef-155"><xref:System.ServiceModel.Channels.TransportBindingElement></span></span>   
<span data-ttu-id="245ef-156"><xref:System.ServiceModel.Channels.CustomBinding></span><span class="sxs-lookup"><span data-stu-id="245ef-156"><xref:System.ServiceModel.Channels.CustomBinding></span></span>   
<span data-ttu-id="245ef-157">[Transporty](../../../../../docs/framework/wcf/feature-details/transports.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-157">[Transports](../../../../../docs/framework/wcf/feature-details/transports.md) </span></span>  
<span data-ttu-id="245ef-158">[Wybieranie transportu](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-158">[Choosing a Transport](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md) </span></span>  
<span data-ttu-id="245ef-159">[Powiązania](../../../../../docs/framework/wcf/bindings.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-159">[Bindings](../../../../../docs/framework/wcf/bindings.md) </span></span>  
<span data-ttu-id="245ef-160">[Rozszerzanie powiązań](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-160">[Extending Bindings](../../../../../docs/framework/wcf/extending/extending-bindings.md) </span></span>  
<span data-ttu-id="245ef-161">[Powiązania niestandardowe](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span><span class="sxs-lookup"><span data-stu-id="245ef-161">[Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md) </span></span>  
[<span data-ttu-id="245ef-162">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="245ef-162">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
