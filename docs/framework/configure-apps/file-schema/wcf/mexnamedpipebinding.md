---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 9ac2b967e33571cbe0b4ad5ee81e13b009ffddd3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772466"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="a6de7-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a6de7-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="a6de7-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) przez nazwany potok.</span><span class="sxs-lookup"><span data-stu-id="a6de7-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="a6de7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6de7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6de7-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a6de7-104">\<bindings></span></span>  
<span data-ttu-id="a6de7-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="a6de7-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6de7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6de7-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6de7-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6de7-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a6de7-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6de7-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6de7-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6de7-109">Attributes</span></span>  
  
|<span data-ttu-id="a6de7-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a6de7-110">Attribute</span></span>|<span data-ttu-id="a6de7-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a6de7-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="a6de7-112">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="a6de7-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a6de7-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6de7-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6de7-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a6de7-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="a6de7-115">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="a6de7-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a6de7-116">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="a6de7-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a6de7-117">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="a6de7-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="a6de7-118">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="a6de7-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="a6de7-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="a6de7-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a6de7-120">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6de7-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a6de7-121">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="a6de7-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a6de7-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6de7-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6de7-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a6de7-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a6de7-124">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="a6de7-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a6de7-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6de7-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6de7-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="a6de7-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a6de7-127">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="a6de7-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a6de7-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="a6de7-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a6de7-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="a6de7-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6de7-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6de7-130">Child Elements</span></span>  
 <span data-ttu-id="a6de7-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="a6de7-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6de7-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6de7-132">Parent Elements</span></span>  
  
|<span data-ttu-id="a6de7-133">Element</span><span class="sxs-lookup"><span data-stu-id="a6de7-133">Element</span></span>|<span data-ttu-id="a6de7-134">Opis</span><span class="sxs-lookup"><span data-stu-id="a6de7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6de7-135">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a6de7-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="a6de7-136">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a6de7-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6de7-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6de7-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="a6de7-138">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a6de7-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="a6de7-139">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="a6de7-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="a6de7-140">Metadane</span><span class="sxs-lookup"><span data-stu-id="a6de7-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="a6de7-141">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a6de7-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a6de7-142">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="a6de7-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a6de7-143">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="a6de7-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a6de7-144">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a6de7-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
