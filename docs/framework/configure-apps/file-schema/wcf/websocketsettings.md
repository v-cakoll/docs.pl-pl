---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226875"
---
# <a name="websocketsettings"></a><span data-ttu-id="4dda0-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="4dda0-101">\<webSocketSettings></span></span>
<span data-ttu-id="4dda0-102">Element konfiguracji, służy do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dda0-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="4dda0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4dda0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4dda0-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4dda0-104">\<bindings></span></span>  
<span data-ttu-id="4dda0-105">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4dda0-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dda0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4dda0-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4dda0-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4dda0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4dda0-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4dda0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4dda0-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4dda0-109">Attributes</span></span>  
  
|<span data-ttu-id="4dda0-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4dda0-110">Attribute</span></span>|<span data-ttu-id="4dda0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4dda0-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4dda0-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="4dda0-112">createNotificationOnConnection</span></span>|<span data-ttu-id="4dda0-113">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="4dda0-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="4dda0-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="4dda0-114">disablePayloadMasking</span></span>|<span data-ttu-id="4dda0-115">Określa, czy maskowania gniazda sieci Web jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="4dda0-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="4dda0-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="4dda0-116">keepAliveInterval</span></span>|<span data-ttu-id="4dda0-117">Określa interwał utrzymywania aktywności Zachowaj.</span><span class="sxs-lookup"><span data-stu-id="4dda0-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="4dda0-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4dda0-118">maxPendingConnections</span></span>|<span data-ttu-id="4dda0-119">Określa maksymalną liczbę połączeń, oczekiwanie na wysłanie w usłudze.</span><span class="sxs-lookup"><span data-stu-id="4dda0-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="4dda0-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="4dda0-120">receiveBufferSize</span></span>|<span data-ttu-id="4dda0-121">Określa rozmiar buforów odbioru.</span><span class="sxs-lookup"><span data-stu-id="4dda0-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="4dda0-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="4dda0-122">sendBufferSize</span></span>|<span data-ttu-id="4dda0-123">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="4dda0-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="4dda0-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="4dda0-124">subProtocol</span></span>|<span data-ttu-id="4dda0-125">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dda0-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="4dda0-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="4dda0-126">transportUsage</span></span>|<span data-ttu-id="4dda0-127">Określa, kiedy należy używać gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dda0-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="4dda0-128">transportUsage atrybutu</span><span class="sxs-lookup"><span data-stu-id="4dda0-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="4dda0-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="4dda0-129">Value</span></span>|<span data-ttu-id="4dda0-130">Opis</span><span class="sxs-lookup"><span data-stu-id="4dda0-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4dda0-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="4dda0-131">WhenDuplex</span></span>|<span data-ttu-id="4dda0-132">Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4dda0-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="4dda0-133">zawsze</span><span class="sxs-lookup"><span data-stu-id="4dda0-133">Always</span></span>|<span data-ttu-id="4dda0-134">Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="4dda0-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="4dda0-135">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="4dda0-135">Never</span></span>|<span data-ttu-id="4dda0-136">Nigdy nie używaj protokołu Websocket.</span><span class="sxs-lookup"><span data-stu-id="4dda0-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4dda0-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4dda0-137">Child Elements</span></span>  
 <span data-ttu-id="4dda0-138">Brak</span><span class="sxs-lookup"><span data-stu-id="4dda0-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4dda0-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4dda0-139">Parent Elements</span></span>  
  
|<span data-ttu-id="4dda0-140">Element</span><span class="sxs-lookup"><span data-stu-id="4dda0-140">Element</span></span>|<span data-ttu-id="4dda0-141">Opis</span><span class="sxs-lookup"><span data-stu-id="4dda0-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dda0-142">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4dda0-142">\<netHttpBinding></span></span>|<span data-ttu-id="4dda0-143">Określa elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4dda0-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4dda0-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="4dda0-144">Example</span></span>  
 <span data-ttu-id="4dda0-145">Poniższy przykład pokazuje, jak używać \<webSocketSettings > element.</span><span class="sxs-lookup"><span data-stu-id="4dda0-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4dda0-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dda0-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="4dda0-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4dda0-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4dda0-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4dda0-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4dda0-149">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="4dda0-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4dda0-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4dda0-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
