---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430338"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="e9718-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="e9718-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="e9718-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e9718-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="e9718-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9718-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9718-104">&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e9718-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e9718-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="e9718-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e9718-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="e9718-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9718-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9718-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9718-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9718-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e9718-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9718-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9718-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9718-110">Attributes</span></span>  
  
|<span data-ttu-id="e9718-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e9718-111">Attribute</span></span>|<span data-ttu-id="e9718-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e9718-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e9718-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="e9718-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e9718-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9718-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9718-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e9718-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="e9718-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="e9718-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e9718-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="e9718-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e9718-118">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="e9718-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e9718-119">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e9718-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e9718-120">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="e9718-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e9718-121">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9718-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9718-122">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e9718-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e9718-123">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="e9718-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e9718-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9718-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9718-125">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="e9718-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e9718-126">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="e9718-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e9718-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="e9718-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e9718-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="e9718-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9718-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9718-129">Child Elements</span></span>  
 <span data-ttu-id="e9718-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="e9718-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9718-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9718-131">Parent Elements</span></span>  
  
|<span data-ttu-id="e9718-132">Element</span><span class="sxs-lookup"><span data-stu-id="e9718-132">Element</span></span>|<span data-ttu-id="e9718-133">Opis</span><span class="sxs-lookup"><span data-stu-id="e9718-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9718-134">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="e9718-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="e9718-135">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e9718-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9718-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9718-136">Remarks</span></span>  
 <span data-ttu-id="e9718-137">To powiązanie jest zasadniczo `WSHttpBinding` powiązaniem, które obsługuje zabezpieczenia na poziomie transportu przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e9718-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="e9718-138">Aby uzyskać więcej informacji o konfigurowaniu i używaniu takiego punktu końcowego metadanych, zobacz [How to: Configure a custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: pobieranie Metadata in a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)i Sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="e9718-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9718-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9718-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="e9718-140">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e9718-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="e9718-141">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="e9718-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="e9718-142">Instrukcje: konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="e9718-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="e9718-143">Instrukcje: pobieranie metadanych przez powiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="e9718-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="e9718-144">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="e9718-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="e9718-145">Metadane</span><span class="sxs-lookup"><span data-stu-id="e9718-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="e9718-146">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e9718-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e9718-147">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="e9718-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e9718-148">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="e9718-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e9718-149">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="e9718-149">\<binding></span></span>](bindings.md)
