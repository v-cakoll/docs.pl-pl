---
title: '&lt;mexNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 90e0a5afc1f1fa4315eab1cd8abdd8840bfe49b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677071"
---
# <a name="ltmexnamedpipebindinggt"></a><span data-ttu-id="fb79e-102">&lt;mexNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="fb79e-102">&lt;mexNamedPipeBinding&gt;</span></span>
<span data-ttu-id="fb79e-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) przez nazwany potok.</span><span class="sxs-lookup"><span data-stu-id="fb79e-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="fb79e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fb79e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb79e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fb79e-105">\<bindings></span></span>  
<span data-ttu-id="fb79e-106">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="fb79e-106">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb79e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb79e-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb79e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fb79e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb79e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fb79e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb79e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fb79e-110">Attributes</span></span>  
  
|<span data-ttu-id="fb79e-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fb79e-111">Attribute</span></span>|<span data-ttu-id="fb79e-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fb79e-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="fb79e-113">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="fb79e-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fb79e-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fb79e-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb79e-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fb79e-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="fb79e-116">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="fb79e-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fb79e-117">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="fb79e-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fb79e-118">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="fb79e-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="fb79e-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="fb79e-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="fb79e-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="fb79e-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fb79e-121">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="fb79e-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="fb79e-122">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="fb79e-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fb79e-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fb79e-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb79e-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fb79e-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fb79e-125">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="fb79e-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fb79e-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fb79e-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb79e-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="fb79e-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="fb79e-128">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="fb79e-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fb79e-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="fb79e-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb79e-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="fb79e-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb79e-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fb79e-131">Child Elements</span></span>  
 <span data-ttu-id="fb79e-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="fb79e-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb79e-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fb79e-133">Parent Elements</span></span>  
  
|<span data-ttu-id="fb79e-134">Element</span><span class="sxs-lookup"><span data-stu-id="fb79e-134">Element</span></span>|<span data-ttu-id="fb79e-135">Opis</span><span class="sxs-lookup"><span data-stu-id="fb79e-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb79e-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="fb79e-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="fb79e-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fb79e-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb79e-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb79e-138">See also</span></span>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="fb79e-139">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="fb79e-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="fb79e-140">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="fb79e-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="fb79e-141">Metadane</span><span class="sxs-lookup"><span data-stu-id="fb79e-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="fb79e-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="fb79e-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="fb79e-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="fb79e-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fb79e-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="fb79e-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fb79e-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="fb79e-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
