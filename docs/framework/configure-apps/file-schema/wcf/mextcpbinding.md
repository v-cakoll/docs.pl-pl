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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ef9df72d06c598cc641d884dadbf9d4f5cee9f5b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="083cf-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="083cf-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="083cf-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="083cf-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="083cf-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="083cf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="083cf-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="083cf-105">\<bindings></span></span>  
<span data-ttu-id="083cf-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="083cf-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="083cf-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="083cf-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="083cf-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="083cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="083cf-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="083cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="083cf-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="083cf-110">Attributes</span></span>  
  
|<span data-ttu-id="083cf-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="083cf-111">Attribute</span></span>|<span data-ttu-id="083cf-112">Opis</span><span class="sxs-lookup"><span data-stu-id="083cf-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="083cf-113">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="083cf-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="083cf-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="083cf-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="083cf-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="083cf-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="083cf-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="083cf-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="083cf-117">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="083cf-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="083cf-118">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="083cf-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="083cf-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="083cf-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="083cf-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="083cf-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="083cf-121">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="083cf-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="083cf-122">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="083cf-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="083cf-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="083cf-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="083cf-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="083cf-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="083cf-125">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="083cf-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="083cf-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="083cf-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="083cf-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="083cf-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="083cf-128">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="083cf-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="083cf-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="083cf-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="083cf-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="083cf-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="083cf-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="083cf-131">Child Elements</span></span>  
 <span data-ttu-id="083cf-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="083cf-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="083cf-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="083cf-133">Parent Elements</span></span>  
  
|<span data-ttu-id="083cf-134">Element</span><span class="sxs-lookup"><span data-stu-id="083cf-134">Element</span></span>|<span data-ttu-id="083cf-135">Opis</span><span class="sxs-lookup"><span data-stu-id="083cf-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="083cf-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="083cf-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="083cf-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="083cf-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="083cf-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="083cf-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="083cf-139">Porady: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="083cf-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="083cf-140">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="083cf-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="083cf-141">Metadane</span><span class="sxs-lookup"><span data-stu-id="083cf-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="083cf-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="083cf-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="083cf-143">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="083cf-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="083cf-144">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="083cf-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="083cf-145">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="083cf-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
