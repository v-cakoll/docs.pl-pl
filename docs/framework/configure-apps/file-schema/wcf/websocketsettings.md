---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732552"
---
# <a name="websocketsettings"></a><span data-ttu-id="aef9e-101">\<webSocketSettings ></span><span class="sxs-lookup"><span data-stu-id="aef9e-101">\<webSocketSettings></span></span>
<span data-ttu-id="aef9e-102">Element konfiguracji służący do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aef9e-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="aef9e-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="aef9e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="aef9e-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="aef9e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="aef9e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="aef9e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="aef9e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<protokół HttpBinding**](nethttpbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="aef9e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="aef9e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="aef9e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="aef9e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="aef9e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aef9e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="aef9e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aef9e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aef9e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aef9e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aef9e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aef9e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aef9e-112">Attributes</span></span>  
  
|<span data-ttu-id="aef9e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aef9e-113">Attribute</span></span>|<span data-ttu-id="aef9e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aef9e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aef9e-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="aef9e-115">createNotificationOnConnection</span></span>|<span data-ttu-id="aef9e-116">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="aef9e-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="aef9e-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="aef9e-117">disablePayloadMasking</span></span>|<span data-ttu-id="aef9e-118">Określa, czy maskowanie gniazda sieci Web jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="aef9e-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="aef9e-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="aef9e-119">keepAliveInterval</span></span>|<span data-ttu-id="aef9e-120">Określa interwał utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="aef9e-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="aef9e-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="aef9e-121">maxPendingConnections</span></span>|<span data-ttu-id="aef9e-122">Określa maksymalną liczbę połączeń oczekujących na wysłanie usługi.</span><span class="sxs-lookup"><span data-stu-id="aef9e-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="aef9e-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="aef9e-123">receiveBufferSize</span></span>|<span data-ttu-id="aef9e-124">Określa rozmiar buforu odbioru.</span><span class="sxs-lookup"><span data-stu-id="aef9e-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="aef9e-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="aef9e-125">sendBufferSize</span></span>|<span data-ttu-id="aef9e-126">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="aef9e-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="aef9e-127">Podprotokół</span><span class="sxs-lookup"><span data-stu-id="aef9e-127">subProtocol</span></span>|<span data-ttu-id="aef9e-128">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aef9e-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="aef9e-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="aef9e-129">transportUsage</span></span>|<span data-ttu-id="aef9e-130">Określa, kiedy należy używać gniazd sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aef9e-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="aef9e-131">transportUsage — atrybut</span><span class="sxs-lookup"><span data-stu-id="aef9e-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="aef9e-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="aef9e-132">Value</span></span>|<span data-ttu-id="aef9e-133">Opis</span><span class="sxs-lookup"><span data-stu-id="aef9e-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aef9e-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="aef9e-134">WhenDuplex</span></span>|<span data-ttu-id="aef9e-135">Użyj protokołu gniazda sieci Web, gdy kontrakt jest w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="aef9e-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="aef9e-136">stałego</span><span class="sxs-lookup"><span data-stu-id="aef9e-136">Always</span></span>|<span data-ttu-id="aef9e-137">Zawsze używaj protokołu gniazda internetowego niezależnie od kontraktu.</span><span class="sxs-lookup"><span data-stu-id="aef9e-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="aef9e-138">Ustawione</span><span class="sxs-lookup"><span data-stu-id="aef9e-138">Never</span></span>|<span data-ttu-id="aef9e-139">Nigdy nie używaj protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="aef9e-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aef9e-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aef9e-140">Child Elements</span></span>  
 <span data-ttu-id="aef9e-141">Brak</span><span class="sxs-lookup"><span data-stu-id="aef9e-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aef9e-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aef9e-142">Parent Elements</span></span>  
  
|<span data-ttu-id="aef9e-143">Element</span><span class="sxs-lookup"><span data-stu-id="aef9e-143">Element</span></span>|<span data-ttu-id="aef9e-144">Opis</span><span class="sxs-lookup"><span data-stu-id="aef9e-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aef9e-145">\<> protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="aef9e-145">\<netHttpBinding></span></span>|<span data-ttu-id="aef9e-146">Określa protokół HttpBinding</span><span class="sxs-lookup"><span data-stu-id="aef9e-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aef9e-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="aef9e-147">Example</span></span>  
 <span data-ttu-id="aef9e-148">Poniższy przykład pokazuje, jak używać elementu \<webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="aef9e-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aef9e-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aef9e-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="aef9e-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="aef9e-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aef9e-151">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="aef9e-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aef9e-152">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="aef9e-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aef9e-153">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="aef9e-153">\<binding></span></span>](bindings.md)
