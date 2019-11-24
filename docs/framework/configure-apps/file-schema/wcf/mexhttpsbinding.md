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
# <a name="mexhttpsbinding"></a><span data-ttu-id="2f36b-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="2f36b-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="2f36b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span><span class="sxs-lookup"><span data-stu-id="2f36b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="2f36b-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f36b-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f36b-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2f36b-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2f36b-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2f36b-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2f36b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding>**</span><span class="sxs-lookup"><span data-stu-id="2f36b-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f36b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f36b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f36b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2f36b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2f36b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2f36b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f36b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2f36b-110">Attributes</span></span>  
  
|<span data-ttu-id="2f36b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2f36b-111">Attribute</span></span>|<span data-ttu-id="2f36b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="2f36b-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2f36b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="2f36b-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="2f36b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2f36b-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2f36b-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2f36b-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="2f36b-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="2f36b-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="2f36b-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="2f36b-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="2f36b-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="2f36b-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="2f36b-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="2f36b-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="2f36b-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="2f36b-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="2f36b-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2f36b-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2f36b-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2f36b-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="2f36b-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="2f36b-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="2f36b-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2f36b-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2f36b-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="2f36b-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="2f36b-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="2f36b-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="2f36b-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="2f36b-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="2f36b-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="2f36b-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f36b-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2f36b-129">Child Elements</span></span>  
 <span data-ttu-id="2f36b-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="2f36b-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f36b-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2f36b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2f36b-132">Element</span><span class="sxs-lookup"><span data-stu-id="2f36b-132">Element</span></span>|<span data-ttu-id="2f36b-133">Opis</span><span class="sxs-lookup"><span data-stu-id="2f36b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f36b-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="2f36b-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="2f36b-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="2f36b-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f36b-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f36b-136">Remarks</span></span>  
 <span data-ttu-id="2f36b-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span><span class="sxs-lookup"><span data-stu-id="2f36b-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="2f36b-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="2f36b-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f36b-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f36b-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="2f36b-140">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2f36b-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="2f36b-141">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="2f36b-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="2f36b-142">Instrukcje: konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="2f36b-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="2f36b-143">Instrukcje: pobieranie metadanych przez powiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="2f36b-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="2f36b-144">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="2f36b-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="2f36b-145">Metadane</span><span class="sxs-lookup"><span data-stu-id="2f36b-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="2f36b-146">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2f36b-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2f36b-147">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="2f36b-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2f36b-148">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="2f36b-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2f36b-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="2f36b-149">\<binding></span></span>](bindings.md)
