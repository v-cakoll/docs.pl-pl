---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 298bf27b171772bb039b11b5e5de70e7d45b061d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258457"
---
# <a name="websocketsettings"></a><span data-ttu-id="9746b-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="9746b-101">\<webSocketSettings></span></span>
<span data-ttu-id="9746b-102">Element konfiguracji, służy do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9746b-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="9746b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9746b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9746b-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9746b-104">\<bindings></span></span>  
<span data-ttu-id="9746b-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9746b-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9746b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="9746b-106">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9746b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9746b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="9746b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9746b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9746b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9746b-109">Attributes</span></span>  
  
|<span data-ttu-id="9746b-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9746b-110">Attribute</span></span>|<span data-ttu-id="9746b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9746b-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9746b-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="9746b-112">createNotificationOnConnection</span></span>|<span data-ttu-id="9746b-113">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="9746b-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="9746b-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="9746b-114">disablePayloadMasking</span></span>|<span data-ttu-id="9746b-115">Określa, czy maskowania gniazda sieci Web jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="9746b-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="9746b-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="9746b-116">keepAliveInterval</span></span>|<span data-ttu-id="9746b-117">Określa interwał utrzymywania aktywności Zachowaj.</span><span class="sxs-lookup"><span data-stu-id="9746b-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="9746b-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="9746b-118">maxPendingConnections</span></span>|<span data-ttu-id="9746b-119">Określa maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="9746b-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="9746b-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="9746b-120">receiveBufferSize</span></span>|<span data-ttu-id="9746b-121">Określa rozmiar buforów odbioru.</span><span class="sxs-lookup"><span data-stu-id="9746b-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="9746b-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="9746b-122">sendBufferSize</span></span>|<span data-ttu-id="9746b-123">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="9746b-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="9746b-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="9746b-124">subProtocol</span></span>|<span data-ttu-id="9746b-125">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9746b-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="9746b-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="9746b-126">transportUsage</span></span>|<span data-ttu-id="9746b-127">Określa, kiedy należy używać gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9746b-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="9746b-128">transportUsage atrybutu</span><span class="sxs-lookup"><span data-stu-id="9746b-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="9746b-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="9746b-129">Value</span></span>|<span data-ttu-id="9746b-130">Opis</span><span class="sxs-lookup"><span data-stu-id="9746b-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9746b-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="9746b-131">WhenDuplex</span></span>|<span data-ttu-id="9746b-132">Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9746b-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="9746b-133">zawsze</span><span class="sxs-lookup"><span data-stu-id="9746b-133">Always</span></span>|<span data-ttu-id="9746b-134">Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="9746b-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="9746b-135">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="9746b-135">Never</span></span>|<span data-ttu-id="9746b-136">Nigdy nie używaj protokołu Websocket.</span><span class="sxs-lookup"><span data-stu-id="9746b-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9746b-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9746b-137">Child Elements</span></span>  
 <span data-ttu-id="9746b-138">Brak</span><span class="sxs-lookup"><span data-stu-id="9746b-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9746b-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9746b-139">Parent Elements</span></span>  
  
|<span data-ttu-id="9746b-140">Element</span><span class="sxs-lookup"><span data-stu-id="9746b-140">Element</span></span>|<span data-ttu-id="9746b-141">Opis</span><span class="sxs-lookup"><span data-stu-id="9746b-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9746b-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9746b-142">\<netHttpBinding></span></span>|<span data-ttu-id="9746b-143">Określa elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9746b-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9746b-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="9746b-144">Example</span></span>  
 <span data-ttu-id="9746b-145">Poniższy przykład pokazuje, jak używać \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="9746b-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a><span data-ttu-id="9746b-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9746b-146">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="9746b-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9746b-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9746b-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="9746b-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9746b-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="9746b-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9746b-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9746b-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
