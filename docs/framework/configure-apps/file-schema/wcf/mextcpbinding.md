---
title: '&lt;mexTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: dbe9e6c3b7a515ee4b5bb147f973423df0f175ea
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187702"
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="5e1ff-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="5e1ff-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="5e1ff-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="5e1ff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5e1ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e1ff-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5e1ff-105">\<bindings></span></span>  
<span data-ttu-id="5e1ff-106">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="5e1ff-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e1ff-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e1ff-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e1ff-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5e1ff-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5e1ff-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e1ff-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5e1ff-110">Attributes</span></span>  
  
|<span data-ttu-id="5e1ff-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5e1ff-111">Attribute</span></span>|<span data-ttu-id="5e1ff-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5e1ff-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="5e1ff-113">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="5e1ff-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5e1ff-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="5e1ff-116">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="5e1ff-117">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="5e1ff-118">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="5e1ff-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="5e1ff-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="5e1ff-121">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5e1ff-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="5e1ff-122">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="5e1ff-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5e1ff-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="5e1ff-125">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="5e1ff-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5e1ff-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="5e1ff-128">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="5e1ff-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="5e1ff-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e1ff-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5e1ff-131">Child Elements</span></span>  
 <span data-ttu-id="5e1ff-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e1ff-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5e1ff-133">Parent Elements</span></span>  
  
|<span data-ttu-id="5e1ff-134">Element</span><span class="sxs-lookup"><span data-stu-id="5e1ff-134">Element</span></span>|<span data-ttu-id="5e1ff-135">Opis</span><span class="sxs-lookup"><span data-stu-id="5e1ff-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e1ff-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="5e1ff-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="5e1ff-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="5e1ff-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e1ff-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e1ff-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="5e1ff-139">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5e1ff-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="5e1ff-140">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="5e1ff-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="5e1ff-141">Metadane</span><span class="sxs-lookup"><span data-stu-id="5e1ff-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="5e1ff-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="5e1ff-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5e1ff-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="5e1ff-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5e1ff-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="5e1ff-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="5e1ff-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="5e1ff-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
