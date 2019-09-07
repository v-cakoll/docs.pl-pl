---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 80784f40130e572ae374bd9b26e701360dbfcaa5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399131"
---
# <a name="websocketsettings"></a><span data-ttu-id="6148c-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="6148c-101">\<webSocketSettings></span></span>
<span data-ttu-id="6148c-102">Element konfiguracji służący do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6148c-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="6148c-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6148c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6148c-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6148c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6148c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6148c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6148c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> protokołu HttpBinding**](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6148c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="6148c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="6148c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6148c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webSocketSettings >**</span><span class="sxs-lookup"><span data-stu-id="6148c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6148c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="6148c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6148c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6148c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6148c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6148c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6148c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6148c-112">Attributes</span></span>  
  
|<span data-ttu-id="6148c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6148c-113">Attribute</span></span>|<span data-ttu-id="6148c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6148c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6148c-115">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="6148c-115">createNotificationOnConnection</span></span>|<span data-ttu-id="6148c-116">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="6148c-116">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="6148c-117">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="6148c-117">disablePayloadMasking</span></span>|<span data-ttu-id="6148c-118">Określa, czy maskowanie gniazda sieci Web jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="6148c-118">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="6148c-119">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="6148c-119">keepAliveInterval</span></span>|<span data-ttu-id="6148c-120">Określa interwał utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="6148c-120">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="6148c-121">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="6148c-121">maxPendingConnections</span></span>|<span data-ttu-id="6148c-122">Określa maksymalną liczbę połączeń oczekujących na wysłanie usługi.</span><span class="sxs-lookup"><span data-stu-id="6148c-122">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="6148c-123">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="6148c-123">receiveBufferSize</span></span>|<span data-ttu-id="6148c-124">Określa rozmiar buforu odbioru.</span><span class="sxs-lookup"><span data-stu-id="6148c-124">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="6148c-125">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="6148c-125">sendBufferSize</span></span>|<span data-ttu-id="6148c-126">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="6148c-126">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="6148c-127">subProtocol</span><span class="sxs-lookup"><span data-stu-id="6148c-127">subProtocol</span></span>|<span data-ttu-id="6148c-128">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6148c-128">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="6148c-129">transportUsage</span><span class="sxs-lookup"><span data-stu-id="6148c-129">transportUsage</span></span>|<span data-ttu-id="6148c-130">Określa, kiedy należy używać gniazd sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6148c-130">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="6148c-131">transportUsage — atrybut</span><span class="sxs-lookup"><span data-stu-id="6148c-131">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="6148c-132">Wartość</span><span class="sxs-lookup"><span data-stu-id="6148c-132">Value</span></span>|<span data-ttu-id="6148c-133">Opis</span><span class="sxs-lookup"><span data-stu-id="6148c-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6148c-134">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="6148c-134">WhenDuplex</span></span>|<span data-ttu-id="6148c-135">Użyj protokołu gniazda sieci Web, gdy kontrakt jest w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="6148c-135">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="6148c-136">zawsze</span><span class="sxs-lookup"><span data-stu-id="6148c-136">Always</span></span>|<span data-ttu-id="6148c-137">Zawsze używaj protokołu gniazda internetowego niezależnie od kontraktu.</span><span class="sxs-lookup"><span data-stu-id="6148c-137">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="6148c-138">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="6148c-138">Never</span></span>|<span data-ttu-id="6148c-139">Nigdy nie używaj protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6148c-139">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6148c-140">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6148c-140">Child Elements</span></span>  
 <span data-ttu-id="6148c-141">Brak</span><span class="sxs-lookup"><span data-stu-id="6148c-141">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6148c-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6148c-142">Parent Elements</span></span>  
  
|<span data-ttu-id="6148c-143">Element</span><span class="sxs-lookup"><span data-stu-id="6148c-143">Element</span></span>|<span data-ttu-id="6148c-144">Opis</span><span class="sxs-lookup"><span data-stu-id="6148c-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6148c-145">\<> protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="6148c-145">\<netHttpBinding></span></span>|<span data-ttu-id="6148c-146">Określa protokół HttpBinding</span><span class="sxs-lookup"><span data-stu-id="6148c-146">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6148c-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="6148c-147">Example</span></span>  
 <span data-ttu-id="6148c-148">Poniższy przykład pokazuje, \<jak używać elementu webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="6148c-148">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6148c-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6148c-149">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="6148c-150">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6148c-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6148c-151">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="6148c-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6148c-152">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="6148c-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6148c-153">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="6148c-153">\<binding></span></span>](../../../misc/binding.md)
