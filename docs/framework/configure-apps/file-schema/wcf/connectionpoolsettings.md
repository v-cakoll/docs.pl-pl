---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400481"
---
# \<connectionPoolSettings>
<span data-ttu-id="7cf71-101">Określa dodatkowe ustawienia puli połączeń dla powiązania nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="7cf71-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="7cf71-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cf71-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cf71-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7cf71-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7cf71-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7cf71-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cf71-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7cf71-105">Attributes</span></span>  
  
|<span data-ttu-id="7cf71-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7cf71-106">Attribute</span></span>|<span data-ttu-id="7cf71-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7cf71-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="7cf71-108">Ciąg określający nazwę puli połączeń używanej dla kanałów wychodzących.</span><span class="sxs-lookup"><span data-stu-id="7cf71-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="7cf71-109">W trybie przesyłania strumieniowego połączenia nie są udostępniane, co oznacza, że buforowanie połączeń jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="7cf71-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="7cf71-110">Wartość domyślna to ciąg "default".</span><span class="sxs-lookup"><span data-stu-id="7cf71-110">The default is a "default" string.</span></span> <span data-ttu-id="7cf71-111">Możesz zmodyfikować tę wartość, aby wyizolować połączenia dla określonego klienta w oddzielnych grupach.</span><span class="sxs-lookup"><span data-stu-id="7cf71-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="7cf71-112">Wartość dodatnia <xref:System.TimeSpan> , która określa maksymalny czas bezczynności połączenia przed jego rozłączeniem.</span><span class="sxs-lookup"><span data-stu-id="7cf71-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="7cf71-113">Wartość domyślna to 00:02:00.</span><span class="sxs-lookup"><span data-stu-id="7cf71-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="7cf71-114">Dodatnia liczba całkowita, która określa maksymalną liczbę połączeń ze zdalnym punktem końcowym inicjowanym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="7cf71-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="7cf71-115">Połączenia przekraczające limit są umieszczane w kolejce do momentu udostępnienia odstępu poniżej limitu.</span><span class="sxs-lookup"><span data-stu-id="7cf71-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="7cf71-116">`idleTimeout`Ogranicza czas, w którym połączenia pozostają w kolejce przed zgłoszeniem wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7cf71-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="7cf71-117">Wartość domyślna to 10.</span><span class="sxs-lookup"><span data-stu-id="7cf71-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="7cf71-118">Ten atrybut ogranicza liczbę jednoczesnych aktywnych połączeń z klienta do określonego punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="7cf71-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="7cf71-119">W przypadku przekroczenia tej wartości przy użyciu większej liczby aktywnych połączeń z klientem usługa może nie odpowiadać na klienta.</span><span class="sxs-lookup"><span data-stu-id="7cf71-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="7cf71-120">W takim przypadku ta wartość powinna zostać zmieniona, aby przekroczyć maksymalną dozwoloną liczbę równoczesnych połączeń klienta do określonego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7cf71-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cf71-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7cf71-121">Child Elements</span></span>  
 <span data-ttu-id="7cf71-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="7cf71-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cf71-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7cf71-123">Parent Elements</span></span>  
  
|<span data-ttu-id="7cf71-124">Element</span><span class="sxs-lookup"><span data-stu-id="7cf71-124">Element</span></span>|<span data-ttu-id="7cf71-125">Opis</span><span class="sxs-lookup"><span data-stu-id="7cf71-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="7cf71-126">Definiuje transport, który powoduje, że kanał przesyła komunikaty przy użyciu nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="7cf71-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cf71-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cf71-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7cf71-128">Transporty</span><span class="sxs-lookup"><span data-stu-id="7cf71-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="7cf71-129">Wybieranie transportu</span><span class="sxs-lookup"><span data-stu-id="7cf71-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="7cf71-130">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7cf71-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7cf71-131">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="7cf71-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7cf71-132">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="7cf71-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
