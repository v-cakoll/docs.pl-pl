---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 79c3c68d69bf3cf5a018e6cf62f34e5ec2ce0cd5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738939"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="7aab6-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="7aab6-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="7aab6-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7aab6-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="7aab6-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7aab6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7aab6-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7aab6-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7aab6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="7aab6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7aab6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="7aab6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aab6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7aab6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7aab6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7aab6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7aab6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7aab6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7aab6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7aab6-110">Attributes</span></span>  
  
|<span data-ttu-id="7aab6-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7aab6-111">Attribute</span></span>|<span data-ttu-id="7aab6-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7aab6-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7aab6-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="7aab6-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7aab6-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7aab6-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7aab6-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7aab6-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="7aab6-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="7aab6-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7aab6-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="7aab6-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7aab6-118">Każde powiązanie ma atrybut `name` i `namespace`, który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="7aab6-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="7aab6-119">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7aab6-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="7aab6-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="7aab6-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7aab6-121">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7aab6-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7aab6-122">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="7aab6-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7aab6-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7aab6-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7aab6-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7aab6-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7aab6-125">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="7aab6-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7aab6-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7aab6-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7aab6-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7aab6-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7aab6-128">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="7aab6-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7aab6-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7aab6-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7aab6-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7aab6-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7aab6-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7aab6-131">Child Elements</span></span>  
 <span data-ttu-id="7aab6-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="7aab6-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7aab6-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7aab6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="7aab6-134">Element</span><span class="sxs-lookup"><span data-stu-id="7aab6-134">Element</span></span>|<span data-ttu-id="7aab6-135">Opis</span><span class="sxs-lookup"><span data-stu-id="7aab6-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7aab6-136">> powiązań\<</span><span class="sxs-lookup"><span data-stu-id="7aab6-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="7aab6-137">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7aab6-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7aab6-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7aab6-138">Remarks</span></span>  
 <span data-ttu-id="7aab6-139">To powiązanie jest zasadniczo `WSHttpBinding` powiązaniem, które obsługuje zabezpieczenia na poziomie transportu przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="7aab6-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="7aab6-140">Aby uzyskać więcej informacji o konfigurowaniu i używaniu takiego punktu końcowego metadanych, zobacz [How to: Configure a custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: pobieranie metadatas in a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)i Sampleal [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md) .</span><span class="sxs-lookup"><span data-stu-id="7aab6-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aab6-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7aab6-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="7aab6-142">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7aab6-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="7aab6-143">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="7aab6-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="7aab6-144">Instrukcje: konfigurowanie niestandardowego powiązania WS-Metadata Exchange</span><span class="sxs-lookup"><span data-stu-id="7aab6-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="7aab6-145">Instrukcje: pobieranie metadanych przez powiązanie inne niż wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="7aab6-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="7aab6-146">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="7aab6-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="7aab6-147">Metadane</span><span class="sxs-lookup"><span data-stu-id="7aab6-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="7aab6-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7aab6-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7aab6-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7aab6-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7aab6-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7aab6-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7aab6-151">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="7aab6-151">\<binding></span></span>](bindings.md)
