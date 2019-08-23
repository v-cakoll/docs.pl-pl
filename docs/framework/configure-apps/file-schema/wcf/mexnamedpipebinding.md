---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 0d0904c02e31def1b5264bec9f61eac0c9a8e964
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931232"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="25754-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="25754-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="25754-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="25754-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="25754-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="25754-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="25754-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="25754-104">\<bindings></span></span>  
<span data-ttu-id="25754-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="25754-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25754-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="25754-106">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25754-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25754-107">Attributes and Elements</span></span>  
 <span data-ttu-id="25754-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25754-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25754-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25754-109">Attributes</span></span>  
  
|<span data-ttu-id="25754-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="25754-110">Attribute</span></span>|<span data-ttu-id="25754-111">Opis</span><span class="sxs-lookup"><span data-stu-id="25754-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="25754-112"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="25754-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="25754-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="25754-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25754-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="25754-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="25754-115">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="25754-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="25754-116">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="25754-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="25754-117">Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="25754-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="25754-118">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="25754-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="25754-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="25754-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="25754-120">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="25754-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="25754-121"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="25754-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="25754-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="25754-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25754-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="25754-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="25754-124"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="25754-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="25754-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="25754-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25754-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="25754-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="25754-127"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="25754-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="25754-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="25754-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25754-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="25754-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25754-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25754-130">Child Elements</span></span>  
 <span data-ttu-id="25754-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="25754-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25754-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25754-132">Parent Elements</span></span>  
  
|<span data-ttu-id="25754-133">Element</span><span class="sxs-lookup"><span data-stu-id="25754-133">Element</span></span>|<span data-ttu-id="25754-134">Opis</span><span class="sxs-lookup"><span data-stu-id="25754-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25754-135">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="25754-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="25754-136">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="25754-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25754-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25754-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="25754-138">Instrukcje: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="25754-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="25754-139">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="25754-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="25754-140">Metadane</span><span class="sxs-lookup"><span data-stu-id="25754-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="25754-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="25754-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="25754-142">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="25754-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="25754-143">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="25754-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="25754-144">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="25754-144">\<binding></span></span>](../../../misc/binding.md)
