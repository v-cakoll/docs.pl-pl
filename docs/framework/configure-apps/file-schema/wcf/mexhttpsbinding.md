---
title: '&lt;mexHttpsBinding&gt;'
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: d56e90162f2a852ff4d0b66abcf3fe03c4110c37
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48846490"
---
# <a name="ltmexhttpsbindinggt"></a><span data-ttu-id="1fafc-102">&lt;mexHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="1fafc-102">&lt;mexHttpsBinding&gt;</span></span>
<span data-ttu-id="1fafc-103">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1fafc-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="1fafc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1fafc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1fafc-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1fafc-105">\<bindings></span></span>  
<span data-ttu-id="1fafc-106">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="1fafc-106">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fafc-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fafc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fafc-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fafc-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1fafc-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fafc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fafc-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fafc-110">Attributes</span></span>  
  
|<span data-ttu-id="1fafc-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1fafc-111">Attribute</span></span>|<span data-ttu-id="1fafc-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1fafc-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1fafc-113">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1fafc-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1fafc-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1fafc-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1fafc-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1fafc-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="1fafc-116">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1fafc-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1fafc-117">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="1fafc-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1fafc-118">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="1fafc-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="1fafc-119">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="1fafc-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="1fafc-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="1fafc-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1fafc-121">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1fafc-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1fafc-122">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="1fafc-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1fafc-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1fafc-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1fafc-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1fafc-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1fafc-125">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="1fafc-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1fafc-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1fafc-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1fafc-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1fafc-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1fafc-128">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1fafc-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1fafc-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1fafc-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1fafc-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1fafc-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fafc-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fafc-131">Child Elements</span></span>  
 <span data-ttu-id="1fafc-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="1fafc-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fafc-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fafc-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1fafc-134">Element</span><span class="sxs-lookup"><span data-stu-id="1fafc-134">Element</span></span>|<span data-ttu-id="1fafc-135">Opis</span><span class="sxs-lookup"><span data-stu-id="1fafc-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fafc-136">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="1fafc-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="1fafc-137">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1fafc-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fafc-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fafc-138">Remarks</span></span>  
 <span data-ttu-id="1fafc-139">To powiązanie jest zasadniczo `WSHttpBinding` powiązania, który obsługuje zabezpieczenia na poziomie transportu za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1fafc-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="1fafc-140">Aby uzyskać więcej informacji na temat konfigurowania i korzystania z punktu końcowego metadanych, zobacz [jak: Konfigurowanie niestandardowego protokołu WS-Metadata Exchange powiązanie](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [porady: Pobieranie metadanych za pośrednictwem MEX powiązanie inne niż](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)i Przykładowe [niestandardowy bezpieczny punkt końcowy metadanych](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="1fafc-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fafc-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fafc-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>  
 <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>  
 [<span data-ttu-id="1fafc-142">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1fafc-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="1fafc-143">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1fafc-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="1fafc-144">Instrukcje: konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="1fafc-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="1fafc-145">Instrukcje: pobieranie metadanych przez powiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="1fafc-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)  
 [<span data-ttu-id="1fafc-146">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="1fafc-146">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)  
 [<span data-ttu-id="1fafc-147">Metadane</span><span class="sxs-lookup"><span data-stu-id="1fafc-147">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="1fafc-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1fafc-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1fafc-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1fafc-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="1fafc-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1fafc-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="1fafc-151">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="1fafc-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
