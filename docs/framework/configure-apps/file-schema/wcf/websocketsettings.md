---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769749"
---
# <a name="websocketsettings"></a><span data-ttu-id="c2509-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="c2509-101">\<webSocketSettings></span></span>
<span data-ttu-id="c2509-102">Element konfiguracji, służy do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c2509-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="c2509-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c2509-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c2509-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c2509-104">\<bindings></span></span>  
<span data-ttu-id="c2509-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c2509-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2509-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2509-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2509-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2509-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c2509-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2509-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2509-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2509-109">Attributes</span></span>  
  
|<span data-ttu-id="c2509-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2509-110">Attribute</span></span>|<span data-ttu-id="c2509-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c2509-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2509-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="c2509-112">createNotificationOnConnection</span></span>|<span data-ttu-id="c2509-113">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="c2509-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="c2509-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="c2509-114">disablePayloadMasking</span></span>|<span data-ttu-id="c2509-115">Określa, czy maskowania gniazda sieci Web jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="c2509-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="c2509-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="c2509-116">keepAliveInterval</span></span>|<span data-ttu-id="c2509-117">Określa interwał utrzymywania aktywności Zachowaj.</span><span class="sxs-lookup"><span data-stu-id="c2509-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="c2509-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="c2509-118">maxPendingConnections</span></span>|<span data-ttu-id="c2509-119">Określa maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="c2509-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="c2509-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="c2509-120">receiveBufferSize</span></span>|<span data-ttu-id="c2509-121">Określa rozmiar buforów odbioru.</span><span class="sxs-lookup"><span data-stu-id="c2509-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="c2509-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="c2509-122">sendBufferSize</span></span>|<span data-ttu-id="c2509-123">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="c2509-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="c2509-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="c2509-124">subProtocol</span></span>|<span data-ttu-id="c2509-125">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c2509-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="c2509-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="c2509-126">transportUsage</span></span>|<span data-ttu-id="c2509-127">Określa, kiedy należy używać gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c2509-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="c2509-128">transportUsage atrybutu</span><span class="sxs-lookup"><span data-stu-id="c2509-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="c2509-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="c2509-129">Value</span></span>|<span data-ttu-id="c2509-130">Opis</span><span class="sxs-lookup"><span data-stu-id="c2509-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2509-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="c2509-131">WhenDuplex</span></span>|<span data-ttu-id="c2509-132">Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c2509-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="c2509-133">zawsze</span><span class="sxs-lookup"><span data-stu-id="c2509-133">Always</span></span>|<span data-ttu-id="c2509-134">Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="c2509-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="c2509-135">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="c2509-135">Never</span></span>|<span data-ttu-id="c2509-136">Nigdy nie używaj protokołu Websocket.</span><span class="sxs-lookup"><span data-stu-id="c2509-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2509-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2509-137">Child Elements</span></span>  
 <span data-ttu-id="c2509-138">Brak</span><span class="sxs-lookup"><span data-stu-id="c2509-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2509-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2509-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c2509-140">Element</span><span class="sxs-lookup"><span data-stu-id="c2509-140">Element</span></span>|<span data-ttu-id="c2509-141">Opis</span><span class="sxs-lookup"><span data-stu-id="c2509-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2509-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c2509-142">\<netHttpBinding></span></span>|<span data-ttu-id="c2509-143">Określa elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c2509-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2509-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2509-144">Example</span></span>  
 <span data-ttu-id="c2509-145">Poniższy przykład pokazuje, jak używać \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="c2509-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2509-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2509-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="c2509-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c2509-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c2509-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="c2509-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c2509-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="c2509-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c2509-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c2509-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
