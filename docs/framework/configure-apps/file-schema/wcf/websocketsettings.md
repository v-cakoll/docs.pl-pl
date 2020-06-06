---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: fa87a1b0961425d6a9bc84769bef6e87cbc2ce96
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732552"
---
# \<webSocketSettings>
<span data-ttu-id="05f9d-101">Element konfiguracji służący do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="05f9d-101">A configuration element used to specify Web Socket settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webSocketSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="05f9d-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="05f9d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05f9d-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05f9d-103">Attributes and Elements</span></span>  
 <span data-ttu-id="05f9d-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05f9d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05f9d-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05f9d-105">Attributes</span></span>  
  
|<span data-ttu-id="05f9d-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05f9d-106">Attribute</span></span>|<span data-ttu-id="05f9d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="05f9d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05f9d-108">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="05f9d-108">createNotificationOnConnection</span></span>|<span data-ttu-id="05f9d-109">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="05f9d-109">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="05f9d-110">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="05f9d-110">disablePayloadMasking</span></span>|<span data-ttu-id="05f9d-111">Określa, czy maskowanie gniazda sieci Web jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="05f9d-111">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="05f9d-112">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="05f9d-112">keepAliveInterval</span></span>|<span data-ttu-id="05f9d-113">Określa interwał utrzymywania aktywności.</span><span class="sxs-lookup"><span data-stu-id="05f9d-113">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="05f9d-114">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="05f9d-114">maxPendingConnections</span></span>|<span data-ttu-id="05f9d-115">Określa maksymalną liczbę połączeń oczekujących na wysłanie usługi.</span><span class="sxs-lookup"><span data-stu-id="05f9d-115">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="05f9d-116">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="05f9d-116">receiveBufferSize</span></span>|<span data-ttu-id="05f9d-117">Określa rozmiar buforu odbioru.</span><span class="sxs-lookup"><span data-stu-id="05f9d-117">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="05f9d-118">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="05f9d-118">sendBufferSize</span></span>|<span data-ttu-id="05f9d-119">Określa rozmiar buforu wysyłania.</span><span class="sxs-lookup"><span data-stu-id="05f9d-119">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="05f9d-120">Podprotokół</span><span class="sxs-lookup"><span data-stu-id="05f9d-120">subProtocol</span></span>|<span data-ttu-id="05f9d-121">Określa podprotokół gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="05f9d-121">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="05f9d-122">transportUsage</span><span class="sxs-lookup"><span data-stu-id="05f9d-122">transportUsage</span></span>|<span data-ttu-id="05f9d-123">Określa, kiedy należy używać gniazd sieci Web.</span><span class="sxs-lookup"><span data-stu-id="05f9d-123">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="05f9d-124">transportUsage — atrybut</span><span class="sxs-lookup"><span data-stu-id="05f9d-124">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="05f9d-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="05f9d-125">Value</span></span>|<span data-ttu-id="05f9d-126">Opis</span><span class="sxs-lookup"><span data-stu-id="05f9d-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="05f9d-127">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="05f9d-127">WhenDuplex</span></span>|<span data-ttu-id="05f9d-128">Użyj protokołu gniazda sieci Web, gdy kontrakt jest w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="05f9d-128">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="05f9d-129">Zawsze</span><span class="sxs-lookup"><span data-stu-id="05f9d-129">Always</span></span>|<span data-ttu-id="05f9d-130">Zawsze używaj protokołu gniazda internetowego niezależnie od kontraktu.</span><span class="sxs-lookup"><span data-stu-id="05f9d-130">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="05f9d-131">Nigdy</span><span class="sxs-lookup"><span data-stu-id="05f9d-131">Never</span></span>|<span data-ttu-id="05f9d-132">Nigdy nie używaj protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="05f9d-132">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05f9d-133">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05f9d-133">Child Elements</span></span>  
 <span data-ttu-id="05f9d-134">Brak</span><span class="sxs-lookup"><span data-stu-id="05f9d-134">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05f9d-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05f9d-135">Parent Elements</span></span>  
  
|<span data-ttu-id="05f9d-136">Element</span><span class="sxs-lookup"><span data-stu-id="05f9d-136">Element</span></span>|<span data-ttu-id="05f9d-137">Opis</span><span class="sxs-lookup"><span data-stu-id="05f9d-137">Description</span></span>|  
|-------------|-----------------|  
|\<netHttpBinding>|<span data-ttu-id="05f9d-138">Określa protokół HttpBinding</span><span class="sxs-lookup"><span data-stu-id="05f9d-138">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="05f9d-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="05f9d-139">Example</span></span>  
 <span data-ttu-id="05f9d-140">Poniższy przykład pokazuje, jak używać \<webSocketSettings> elementu.</span><span class="sxs-lookup"><span data-stu-id="05f9d-140">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05f9d-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05f9d-141">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [<span data-ttu-id="05f9d-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="05f9d-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="05f9d-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="05f9d-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="05f9d-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="05f9d-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
