---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 5c9dbec13dd0d71ba1b92ea971d067540013b6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940321"
---
# <a name="websocketsettings"></a><span data-ttu-id="e3531-101">\<webSocketSettings></span><span class="sxs-lookup"><span data-stu-id="e3531-101">\<webSocketSettings></span></span>
<span data-ttu-id="e3531-102">Element konfiguracji służący do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e3531-102">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="e3531-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e3531-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e3531-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="e3531-104">\<bindings></span></span>  
<span data-ttu-id="e3531-105">\<> protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="e3531-105">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3531-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3531-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3531-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e3531-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e3531-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e3531-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3531-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e3531-109">Attributes</span></span>  
  
|<span data-ttu-id="e3531-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e3531-110">Attribute</span></span>|<span data-ttu-id="e3531-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e3531-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3531-112">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="e3531-112">createNotificationOnConnection</span></span>|<span data-ttu-id="e3531-113">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="e3531-113">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="e3531-114">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="e3531-114">disablePayloadMasking</span></span>|<span data-ttu-id="e3531-115">Określa, czy maskowanie gniazda sieci Web jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e3531-115">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="e3531-116">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="e3531-116">keepAliveInterval</span></span>|<span data-ttu-id="e3531-117">Określa interwał utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="e3531-117">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="e3531-118">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e3531-118">maxPendingConnections</span></span>|<span data-ttu-id="e3531-119">Określa maksymalną liczbę połączeń oczekujących na wysłanie usługi.</span><span class="sxs-lookup"><span data-stu-id="e3531-119">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="e3531-120">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="e3531-120">receiveBufferSize</span></span>|<span data-ttu-id="e3531-121">Określa rozmiar buforu odbioru.</span><span class="sxs-lookup"><span data-stu-id="e3531-121">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="e3531-122">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="e3531-122">sendBufferSize</span></span>|<span data-ttu-id="e3531-123">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e3531-123">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="e3531-124">subProtocol</span><span class="sxs-lookup"><span data-stu-id="e3531-124">subProtocol</span></span>|<span data-ttu-id="e3531-125">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e3531-125">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="e3531-126">transportUsage</span><span class="sxs-lookup"><span data-stu-id="e3531-126">transportUsage</span></span>|<span data-ttu-id="e3531-127">Określa, kiedy należy używać gniazd sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e3531-127">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="e3531-128">transportUsage — atrybut</span><span class="sxs-lookup"><span data-stu-id="e3531-128">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="e3531-129">Wartość</span><span class="sxs-lookup"><span data-stu-id="e3531-129">Value</span></span>|<span data-ttu-id="e3531-130">Opis</span><span class="sxs-lookup"><span data-stu-id="e3531-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3531-131">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="e3531-131">WhenDuplex</span></span>|<span data-ttu-id="e3531-132">Użyj protokołu gniazda sieci Web, gdy kontrakt jest w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="e3531-132">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="e3531-133">zawsze</span><span class="sxs-lookup"><span data-stu-id="e3531-133">Always</span></span>|<span data-ttu-id="e3531-134">Zawsze używaj protokołu gniazda internetowego niezależnie od kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e3531-134">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="e3531-135">nigdy nie</span><span class="sxs-lookup"><span data-stu-id="e3531-135">Never</span></span>|<span data-ttu-id="e3531-136">Nigdy nie używaj protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e3531-136">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3531-137">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e3531-137">Child Elements</span></span>  
 <span data-ttu-id="e3531-138">Brak</span><span class="sxs-lookup"><span data-stu-id="e3531-138">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3531-139">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e3531-139">Parent Elements</span></span>  
  
|<span data-ttu-id="e3531-140">Element</span><span class="sxs-lookup"><span data-stu-id="e3531-140">Element</span></span>|<span data-ttu-id="e3531-141">Opis</span><span class="sxs-lookup"><span data-stu-id="e3531-141">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e3531-142">\<> protokołu HttpBinding</span><span class="sxs-lookup"><span data-stu-id="e3531-142">\<netHttpBinding></span></span>|<span data-ttu-id="e3531-143">Określa protokół HttpBinding</span><span class="sxs-lookup"><span data-stu-id="e3531-143">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e3531-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3531-144">Example</span></span>  
 <span data-ttu-id="e3531-145">Poniższy przykład pokazuje, \<jak używać elementu webSocketSettings >.</span><span class="sxs-lookup"><span data-stu-id="e3531-145">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3531-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3531-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="e3531-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e3531-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e3531-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e3531-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e3531-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e3531-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e3531-150">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="e3531-150">\<binding></span></span>](../../../misc/binding.md)
