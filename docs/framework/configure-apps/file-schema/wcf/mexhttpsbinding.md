---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430338"
---
# \<mexHttpsBinding>
<span data-ttu-id="1cb0a-101">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="1cb0a-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cb0a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cb0a-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1cb0a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1cb0a-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cb0a-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1cb0a-105">Attributes</span></span>  
  
|<span data-ttu-id="1cb0a-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1cb0a-106">Attribute</span></span>|<span data-ttu-id="1cb0a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1cb0a-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1cb0a-108"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1cb0a-109">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1cb0a-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1cb0a-110">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="1cb0a-111">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1cb0a-112">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1cb0a-113">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1cb0a-114">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1cb0a-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1cb0a-115"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1cb0a-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1cb0a-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1cb0a-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1cb0a-118">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1cb0a-119">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1cb0a-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1cb0a-120">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1cb0a-121"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1cb0a-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="1cb0a-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1cb0a-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cb0a-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1cb0a-124">Child Elements</span></span>  
 <span data-ttu-id="1cb0a-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1cb0a-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1cb0a-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1cb0a-127">Element</span><span class="sxs-lookup"><span data-stu-id="1cb0a-127">Element</span></span>|<span data-ttu-id="1cb0a-128">Opis</span><span class="sxs-lookup"><span data-stu-id="1cb0a-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="1cb0a-129">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cb0a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cb0a-130">Remarks</span></span>  
 <span data-ttu-id="1cb0a-131">To powiązanie jest zasadniczo `WSHttpBinding` powiązaniem, które obsługuje zabezpieczenia na poziomie transportu przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="1cb0a-131">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="1cb0a-132">Aby uzyskać więcej informacji o konfigurowaniu i używaniu takiego punktu końcowego metadanych, zobacz [How to: Configure a custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: pobieranie Metadata in a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)i Sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="1cb0a-132">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb0a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cb0a-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="1cb0a-134">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1cb0a-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="1cb0a-135">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1cb0a-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="1cb0a-136">Instrukcje: Konfigurowanie niestandardowego wiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="1cb0a-136">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="1cb0a-137">Instrukcje: Pobieranie metadanych przez wiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="1cb0a-137">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="1cb0a-138">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="1cb0a-138">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="1cb0a-139">Metadane</span><span class="sxs-lookup"><span data-stu-id="1cb0a-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="1cb0a-140">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1cb0a-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1cb0a-141">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1cb0a-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1cb0a-142">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1cb0a-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
