---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 1aa9512c3d0d52f8cc3c7bd7b82bcfd37c418ce7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151245"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="87f98-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="87f98-101">\<mexHttpBinding></span></span>
<span data-ttu-id="87f98-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="87f98-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="87f98-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87f98-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="87f98-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="87f98-104">\<bindings></span></span>  
<span data-ttu-id="87f98-105">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="87f98-105">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f98-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="87f98-106">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87f98-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87f98-107">Attributes and Elements</span></span>  
 <span data-ttu-id="87f98-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87f98-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87f98-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87f98-109">Attributes</span></span>  
  
|<span data-ttu-id="87f98-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87f98-110">Attribute</span></span>|<span data-ttu-id="87f98-111">Opis</span><span class="sxs-lookup"><span data-stu-id="87f98-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="87f98-112">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="87f98-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="87f98-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87f98-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87f98-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="87f98-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="87f98-115">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="87f98-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="87f98-116">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="87f98-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="87f98-117">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="87f98-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="87f98-118">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="87f98-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="87f98-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="87f98-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="87f98-120">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="87f98-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="87f98-121">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="87f98-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="87f98-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87f98-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87f98-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="87f98-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="87f98-124">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="87f98-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="87f98-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87f98-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87f98-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="87f98-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="87f98-127">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="87f98-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="87f98-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="87f98-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="87f98-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="87f98-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87f98-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87f98-130">Child Elements</span></span>  
 <span data-ttu-id="87f98-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="87f98-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87f98-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87f98-132">Parent Elements</span></span>  
  
|<span data-ttu-id="87f98-133">Element</span><span class="sxs-lookup"><span data-stu-id="87f98-133">Element</span></span>|<span data-ttu-id="87f98-134">Opis</span><span class="sxs-lookup"><span data-stu-id="87f98-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87f98-135">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="87f98-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="87f98-136">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="87f98-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87f98-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87f98-137">Remarks</span></span>  
 <span data-ttu-id="87f98-138">To powiązanie jest zasadniczo `WSHttpBinding` powiązania z wyłączonymi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="87f98-138">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="87f98-139">Obsługuje większość żądań metadanych.</span><span class="sxs-lookup"><span data-stu-id="87f98-139">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f98-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87f98-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="87f98-141">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="87f98-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="87f98-142">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="87f98-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="87f98-143">Metadane</span><span class="sxs-lookup"><span data-stu-id="87f98-143">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="87f98-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="87f98-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="87f98-145">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="87f98-145">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="87f98-146">Konfigurowanie usług i klientów za pomocą wiązań</span><span class="sxs-lookup"><span data-stu-id="87f98-146">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="87f98-147">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="87f98-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
