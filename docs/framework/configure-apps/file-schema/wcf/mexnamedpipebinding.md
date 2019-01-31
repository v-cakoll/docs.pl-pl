---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: f9f6186cc88f2cc0fed8404f9e4d5776d41e2818
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284869"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="1089e-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1089e-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="1089e-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) przez nazwany potok.</span><span class="sxs-lookup"><span data-stu-id="1089e-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="1089e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1089e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1089e-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1089e-104">\<bindings></span></span>  
<span data-ttu-id="1089e-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1089e-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1089e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1089e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1089e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1089e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1089e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1089e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1089e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1089e-109">Attributes</span></span>  
  
|<span data-ttu-id="1089e-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1089e-110">Attribute</span></span>|<span data-ttu-id="1089e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1089e-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1089e-112">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1089e-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1089e-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1089e-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1089e-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1089e-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="1089e-115">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1089e-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1089e-116">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="1089e-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1089e-117">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="1089e-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="1089e-118">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="1089e-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="1089e-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="1089e-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1089e-120">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1089e-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1089e-121">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="1089e-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1089e-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1089e-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1089e-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1089e-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1089e-124">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="1089e-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1089e-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1089e-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1089e-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1089e-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1089e-127">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1089e-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1089e-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1089e-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1089e-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1089e-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1089e-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1089e-130">Child Elements</span></span>  
 <span data-ttu-id="1089e-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="1089e-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1089e-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1089e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="1089e-133">Element</span><span class="sxs-lookup"><span data-stu-id="1089e-133">Element</span></span>|<span data-ttu-id="1089e-134">Opis</span><span class="sxs-lookup"><span data-stu-id="1089e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1089e-135">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1089e-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="1089e-136">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1089e-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1089e-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1089e-137">See also</span></span>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="1089e-138">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1089e-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="1089e-139">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1089e-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="1089e-140">Metadane</span><span class="sxs-lookup"><span data-stu-id="1089e-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="1089e-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1089e-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1089e-142">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1089e-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1089e-143">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1089e-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1089e-144">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1089e-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
