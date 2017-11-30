---
title: '&lt;mexTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4d4b041ba7872a3e66d1177d114ddfb0736e3e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="e205b-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e205b-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="e205b-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="e205b-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="e205b-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e205b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e205b-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e205b-105">\<bindings></span></span>  
<span data-ttu-id="e205b-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="e205b-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e205b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e205b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e205b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e205b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e205b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e205b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e205b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e205b-110">Attributes</span></span>  
  
|<span data-ttu-id="e205b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e205b-111">Attribute</span></span>|<span data-ttu-id="e205b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e205b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e205b-113">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="e205b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e205b-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e205b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e205b-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e205b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="e205b-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="e205b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e205b-117">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e205b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e205b-118">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="e205b-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="e205b-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="e205b-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="e205b-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="e205b-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e205b-121">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e205b-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e205b-122">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="e205b-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e205b-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e205b-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e205b-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e205b-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e205b-125">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="e205b-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e205b-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e205b-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e205b-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e205b-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e205b-128">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e205b-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e205b-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e205b-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e205b-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e205b-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e205b-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e205b-131">Child Elements</span></span>  
 <span data-ttu-id="e205b-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="e205b-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e205b-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e205b-133">Parent Elements</span></span>  
  
|<span data-ttu-id="e205b-134">Element</span><span class="sxs-lookup"><span data-stu-id="e205b-134">Element</span></span>|<span data-ttu-id="e205b-135">Opis</span><span class="sxs-lookup"><span data-stu-id="e205b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e205b-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="e205b-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e205b-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e205b-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e205b-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e205b-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="e205b-139">Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e205b-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="e205b-140">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="e205b-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="e205b-141">Metadane</span><span class="sxs-lookup"><span data-stu-id="e205b-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="e205b-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e205b-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e205b-143">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="e205b-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e205b-144">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e205b-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e205b-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="e205b-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
