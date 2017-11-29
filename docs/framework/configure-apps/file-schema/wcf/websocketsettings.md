---
title: '&lt;webSocketSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2714b27916a47ae8e002ea857c93377736c4eff5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebsocketsettingsgt"></a><span data-ttu-id="38489-102">&lt;webSocketSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="38489-102">&lt;webSocketSettings&gt;</span></span>
<span data-ttu-id="38489-103">Element konfiguracji, służy do określania ustawień gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="38489-103">A configuration element used to specify Web Socket settings.</span></span>  
  
<span data-ttu-id="38489-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="38489-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="38489-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="38489-105">\<bindings></span></span>  
<span data-ttu-id="38489-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="38489-106">\<netHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38489-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="38489-107">Syntax</span></span>  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38489-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="38489-108">Attributes and Elements</span></span>  
 <span data-ttu-id="38489-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="38489-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38489-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="38489-110">Attributes</span></span>  
  
|<span data-ttu-id="38489-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="38489-111">Attribute</span></span>|<span data-ttu-id="38489-112">Opis</span><span class="sxs-lookup"><span data-stu-id="38489-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38489-113">createNotificationOnConnection</span><span class="sxs-lookup"><span data-stu-id="38489-113">createNotificationOnConnection</span></span>|<span data-ttu-id="38489-114">Określa, czy powiadomienie jest wysyłane po nawiązaniu połączenia.</span><span class="sxs-lookup"><span data-stu-id="38489-114">Specifies whether a notification is sent upon connection.</span></span>|  
|<span data-ttu-id="38489-115">disablePayloadMasking</span><span class="sxs-lookup"><span data-stu-id="38489-115">disablePayloadMasking</span></span>|<span data-ttu-id="38489-116">Określa, czy maskowania gniazda sieci Web jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="38489-116">Specifies whether Web Socket masking is disabled.</span></span>|  
|<span data-ttu-id="38489-117">keepAliveInterval</span><span class="sxs-lookup"><span data-stu-id="38489-117">keepAliveInterval</span></span>|<span data-ttu-id="38489-118">Określa interwał keep alive.</span><span class="sxs-lookup"><span data-stu-id="38489-118">Specifies the keep alive interval.</span></span>|  
|<span data-ttu-id="38489-119">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="38489-119">maxPendingConnections</span></span>|<span data-ttu-id="38489-120">Określa maksymalną liczbę połączeń oczekujących na wysyłania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="38489-120">Specifies the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="38489-121">receiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="38489-121">receiveBufferSize</span></span>|<span data-ttu-id="38489-122">Określa rozmiar buforu odbioru.</span><span class="sxs-lookup"><span data-stu-id="38489-122">Specifies the size of the receive buffer.</span></span>|  
|<span data-ttu-id="38489-123">sendBufferSize</span><span class="sxs-lookup"><span data-stu-id="38489-123">sendBufferSize</span></span>|<span data-ttu-id="38489-124">Określa rozmiar buforów wysyłania.</span><span class="sxs-lookup"><span data-stu-id="38489-124">Specifies the size of the send buffer.</span></span>|  
|<span data-ttu-id="38489-125">Podprotokół</span><span class="sxs-lookup"><span data-stu-id="38489-125">subProtocol</span></span>|<span data-ttu-id="38489-126">Określa podprotokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="38489-126">Specifies the Web Socket subprotocol.</span></span>|  
|<span data-ttu-id="38489-127">transportUsage</span><span class="sxs-lookup"><span data-stu-id="38489-127">transportUsage</span></span>|<span data-ttu-id="38489-128">Określa, kiedy należy używać gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="38489-128">Specifies when to use Web Sockets.</span></span>|  
  
## <a name="transportusage-attribute"></a><span data-ttu-id="38489-129">transportUsage atrybutu</span><span class="sxs-lookup"><span data-stu-id="38489-129">transportUsage Attribute</span></span>  
  
|<span data-ttu-id="38489-130">Wartość</span><span class="sxs-lookup"><span data-stu-id="38489-130">Value</span></span>|<span data-ttu-id="38489-131">Opis</span><span class="sxs-lookup"><span data-stu-id="38489-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38489-132">WhenDuplex</span><span class="sxs-lookup"><span data-stu-id="38489-132">WhenDuplex</span></span>|<span data-ttu-id="38489-133">Gdy kontrakt jest dupleksowy, należy użyć protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="38489-133">Use the Web Socket protocol when the contract is duplex.</span></span>|  
|<span data-ttu-id="38489-134">Zawsze</span><span class="sxs-lookup"><span data-stu-id="38489-134">Always</span></span>|<span data-ttu-id="38489-135">Zawsze używaj protokołu gniazda sieci Web, niezależnie od tego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="38489-135">Always use the Web Socket protocol regardless of the contract.</span></span>|  
|<span data-ttu-id="38489-136">Nigdy nie</span><span class="sxs-lookup"><span data-stu-id="38489-136">Never</span></span>|<span data-ttu-id="38489-137">Nigdy nie używaj protokołu gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="38489-137">Never use the Web Socket protocol.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38489-138">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="38489-138">Child Elements</span></span>  
 <span data-ttu-id="38489-139">Brak</span><span class="sxs-lookup"><span data-stu-id="38489-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38489-140">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="38489-140">Parent Elements</span></span>  
  
|<span data-ttu-id="38489-141">Element</span><span class="sxs-lookup"><span data-stu-id="38489-141">Element</span></span>|<span data-ttu-id="38489-142">Opis</span><span class="sxs-lookup"><span data-stu-id="38489-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="38489-143">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="38489-143">\<netHttpBinding></span></span>|<span data-ttu-id="38489-144">Określa elementu NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="38489-144">Specifies the NetHttpBinding</span></span>|  
  
## <a name="example"></a><span data-ttu-id="38489-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="38489-145">Example</span></span>  
 <span data-ttu-id="38489-146">Poniższy przykład przedstawia użycie \<webSocketSettings > elementu.</span><span class="sxs-lookup"><span data-stu-id="38489-146">The following example shows how to use the \<webSocketSettings> element.</span></span>  
  
```xml  
<netHttpBinding>  
        <binding>  
          <webSocketSettings createNotificationOnConnection="true"  
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38489-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38489-147">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="38489-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="38489-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="38489-149">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="38489-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="38489-150">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="38489-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="38489-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="38489-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
