---
title: '&lt;mexHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c78c1d90e10a45245f53f1db0b6400fa0a91d81b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="ab3b8-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ab3b8-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="ab3b8-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="ab3b8-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ab3b8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ab3b8-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ab3b8-105">\<bindings></span></span>  
<span data-ttu-id="ab3b8-106">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="ab3b8-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab3b8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab3b8-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexHttpsBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab3b8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ab3b8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ab3b8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab3b8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ab3b8-110">Attributes</span></span>  
  
|<span data-ttu-id="ab3b8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ab3b8-111">Attribute</span></span>|<span data-ttu-id="ab3b8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="ab3b8-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="ab3b8-113">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="ab3b8-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ab3b8-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="ab3b8-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="ab3b8-117">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="ab3b8-118">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="ab3b8-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="ab3b8-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ab3b8-121">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ab3b8-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="ab3b8-122">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="ab3b8-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ab3b8-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="ab3b8-125">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="ab3b8-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ab3b8-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="ab3b8-128">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="ab3b8-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="ab3b8-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab3b8-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ab3b8-131">Child Elements</span></span>  
 <span data-ttu-id="ab3b8-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab3b8-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab3b8-133">Parent Elements</span></span>  
  
|<span data-ttu-id="ab3b8-134">Element</span><span class="sxs-lookup"><span data-stu-id="ab3b8-134">Element</span></span>|<span data-ttu-id="ab3b8-135">Opis</span><span class="sxs-lookup"><span data-stu-id="ab3b8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab3b8-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="ab3b8-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="ab3b8-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab3b8-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab3b8-138">Remarks</span></span>  
 <span data-ttu-id="ab3b8-139">To powiązanie jest zasadniczo `WSHttpBinding` powiązanie obsługuje zabezpieczeń na poziomie transportu za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="ab3b8-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="ab3b8-140">Aby uzyskać więcej informacji o konfigurowaniu i używaniu punktu końcowego metadanych, zobacz [jak: Konfigurowanie niestandardowych WS-Metadata Exchange powiązanie](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [porady: Pobieranie metadanych przez wiązanie inne niż wymiany](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)i Przykładowe [punktu końcowego metadanych niestandardowy bezpieczny](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="ab3b8-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3b8-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab3b8-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="ab3b8-142">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ab3b8-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="ab3b8-143">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="ab3b8-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="ab3b8-144">Instrukcje: konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="ab3b8-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="ab3b8-145">Instrukcje: pobieranie metadanych przez powiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="ab3b8-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="ab3b8-146">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="ab3b8-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="ab3b8-147">Metadane</span><span class="sxs-lookup"><span data-stu-id="ab3b8-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="ab3b8-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ab3b8-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ab3b8-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="ab3b8-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ab3b8-150">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="ab3b8-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ab3b8-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="ab3b8-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
