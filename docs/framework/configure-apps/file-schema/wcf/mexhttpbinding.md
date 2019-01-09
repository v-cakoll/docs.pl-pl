---
title: '&lt;mexHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: c60fcf5071d52d30c1b6b99a19640a0fdc1265f8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148659"
---
# <a name="ltmexhttpbindinggt"></a><span data-ttu-id="7a643-102">&lt;mexHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7a643-102">&lt;mexHttpBinding&gt;</span></span>
<span data-ttu-id="7a643-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7a643-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="7a643-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7a643-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7a643-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7a643-105">\<bindings></span></span>  
<span data-ttu-id="7a643-106">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7a643-106">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a643-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a643-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a643-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7a643-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7a643-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7a643-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a643-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7a643-110">Attributes</span></span>  
  
|<span data-ttu-id="7a643-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7a643-111">Attribute</span></span>|<span data-ttu-id="7a643-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7a643-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7a643-113">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="7a643-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7a643-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a643-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a643-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a643-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="7a643-116">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a643-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7a643-117">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="7a643-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7a643-118">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="7a643-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7a643-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7a643-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7a643-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="7a643-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7a643-121">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7a643-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7a643-122">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="7a643-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7a643-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a643-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a643-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a643-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7a643-125">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="7a643-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7a643-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a643-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a643-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7a643-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7a643-128">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="7a643-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7a643-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7a643-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7a643-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7a643-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a643-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7a643-131">Child Elements</span></span>  
 <span data-ttu-id="7a643-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="7a643-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a643-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7a643-133">Parent Elements</span></span>  
  
|<span data-ttu-id="7a643-134">Element</span><span class="sxs-lookup"><span data-stu-id="7a643-134">Element</span></span>|<span data-ttu-id="7a643-135">Opis</span><span class="sxs-lookup"><span data-stu-id="7a643-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a643-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="7a643-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7a643-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7a643-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a643-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a643-138">Remarks</span></span>  
 <span data-ttu-id="7a643-139">To powiązanie jest zasadniczo `WSHttpBinding` powiązania z wyłączonymi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="7a643-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="7a643-140">Obsługuje większość żądań metadanych.</span><span class="sxs-lookup"><span data-stu-id="7a643-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a643-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a643-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpBindingElement>  
 [<span data-ttu-id="7a643-142">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7a643-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="7a643-143">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="7a643-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="7a643-144">Metadane</span><span class="sxs-lookup"><span data-stu-id="7a643-144">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="7a643-145">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7a643-145">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="7a643-146">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7a643-146">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="7a643-147">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7a643-147">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="7a643-148">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="7a643-148">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
