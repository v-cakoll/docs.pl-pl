---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 00c6bc45f06d97d4f95bd6be1515d16141be4e1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565920"
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="02e49-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="02e49-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="02e49-103">Element konfiguracji, służy do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="02e49-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="02e49-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="02e49-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="02e49-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="02e49-105">\<bindings></span></span>  
<span data-ttu-id="02e49-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="02e49-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e49-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="02e49-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02e49-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="02e49-108">Attributes and Elements</span></span>  
 <span data-ttu-id="02e49-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="02e49-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02e49-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="02e49-110">Attributes</span></span>  
  
|<span data-ttu-id="02e49-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="02e49-111">Attribute</span></span>|<span data-ttu-id="02e49-112">Opis</span><span class="sxs-lookup"><span data-stu-id="02e49-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02e49-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="02e49-113">createNotificationOnConnection</span></span>|<span data-ttu-id="02e49-114">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="02e49-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="02e49-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="02e49-115">disablePayloadMasking</span></span>|<span data-ttu-id="02e49-116">Określa, czy maskowania gniazda sieci Web jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="02e49-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="02e49-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="02e49-117">keepAliveInterval</span></span>|<span data-ttu-id="02e49-118">Określa interwał utrzymywania aktywności Zachowaj.</span><span class="sxs-lookup"><span data-stu-id="02e49-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="02e49-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="02e49-119">maxPendingConnections</span></span>|<span data-ttu-id="02e49-120">Określa maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="02e49-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="02e49-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="02e49-121">receiveBufferSize</span></span>|<span data-ttu-id="02e49-122">Określa rozmiar buforów odbioru.</span><span class="sxs-lookup"><span data-stu-id="02e49-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="02e49-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="02e49-123">sendBufferSize</span></span>|<span data-ttu-id="02e49-124">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="02e49-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="02e49-125">subProtocol</span><span class="sxs-lookup"><span data-stu-id="02e49-125">subProtocol</span></span>|<span data-ttu-id="02e49-126">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="02e49-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="02e49-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="02e49-127">transportUsage</span></span>|<span data-ttu-id="02e49-128">Określa, kiedy należy używać gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="02e49-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="02e49-129">transportUsage atrybutu</span><span class="sxs-lookup"><span data-stu-id="02e49-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="02e49-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="02e49-130">Value</span></span>|<span data-ttu-id="02e49-131">Opis</span><span class="sxs-lookup"><span data-stu-id="02e49-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="02e49-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="02e49-132">WhenDuplex</span></span>|<span data-ttu-id="02e49-133">Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="02e49-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="02e49-134">zawsze</span><span class="sxs-lookup"><span data-stu-id="02e49-134">Always</span></span>|<span data-ttu-id="02e49-135">Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="02e49-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="02e49-136">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="02e49-136">Never</span></span>|<span data-ttu-id="02e49-137">Nigdy nie używaj protokołu Websocket.</span><span class="sxs-lookup"><span data-stu-id="02e49-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02e49-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="02e49-138">Child Elements</span></span>  
 <span data-ttu-id="02e49-139">Brak</span><span class="sxs-lookup"><span data-stu-id="02e49-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02e49-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="02e49-140">Parent Elements</span></span>  
  
|<span data-ttu-id="02e49-141">Element</span><span class="sxs-lookup"><span data-stu-id="02e49-141">Element</span></span>|<span data-ttu-id="02e49-142">Opis</span><span class="sxs-lookup"><span data-stu-id="02e49-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02e49-143">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="02e49-143">\<netHttpBinding></span></span>|<span data-ttu-id="02e49-144">Określa elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="02e49-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="02e49-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="02e49-145">Example</span></span>  
 <span data-ttu-id="02e49-146">Poniższy przykład pokazuje, jak używać \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="02e49-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="02e49-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02e49-147">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="02e49-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="02e49-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="02e49-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="02e49-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="02e49-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="02e49-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="02e49-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="02e49-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
