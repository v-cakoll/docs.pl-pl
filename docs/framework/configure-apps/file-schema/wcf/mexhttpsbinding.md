---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: d32db2180e06cba6662ed853ab1a259805680ea1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397820"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="bfe00-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="bfe00-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="bfe00-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bfe00-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="bfe00-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfe00-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bfe00-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bfe00-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bfe00-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bfe00-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bfe00-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="bfe00-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfe00-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfe00-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfe00-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bfe00-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bfe00-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bfe00-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfe00-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bfe00-110">Attributes</span></span>  
  
|<span data-ttu-id="bfe00-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bfe00-111">Attribute</span></span>|<span data-ttu-id="bfe00-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bfe00-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bfe00-113"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="bfe00-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bfe00-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bfe00-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfe00-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bfe00-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bfe00-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="bfe00-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bfe00-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="bfe00-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bfe00-118">Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="bfe00-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="bfe00-119">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="bfe00-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="bfe00-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="bfe00-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bfe00-121">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bfe00-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bfe00-122"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="bfe00-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bfe00-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bfe00-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfe00-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bfe00-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bfe00-125"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="bfe00-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bfe00-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bfe00-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfe00-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bfe00-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bfe00-128"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="bfe00-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bfe00-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bfe00-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bfe00-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bfe00-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfe00-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bfe00-131">Child Elements</span></span>  
 <span data-ttu-id="bfe00-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="bfe00-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfe00-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bfe00-133">Parent Elements</span></span>  
  
|<span data-ttu-id="bfe00-134">Element</span><span class="sxs-lookup"><span data-stu-id="bfe00-134">Element</span></span>|<span data-ttu-id="bfe00-135">Opis</span><span class="sxs-lookup"><span data-stu-id="bfe00-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfe00-136">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="bfe00-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bfe00-137">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bfe00-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfe00-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfe00-138">Remarks</span></span>  
 <span data-ttu-id="bfe00-139">To powiązanie jest zasadniczo `WSHttpBinding` powiązaniem, które obsługuje zabezpieczenia na poziomie transportu przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="bfe00-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="bfe00-140">Aby uzyskać więcej informacji o konfigurowaniu i używaniu takiego punktu końcowego [metadanych, zobacz How to: Skonfiguruj niestandardowe powiązanie](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)WS-Metadata Exchange, [jak: Pobieranie metadanych za pośrednictwem powiązania](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)niezwiązanego z elementem MEX i przykładowym, [niestandardowym bezpiecznym punktem końcowym metadanych](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="bfe00-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfe00-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfe00-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="bfe00-142">Instrukcje: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bfe00-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bfe00-143">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bfe00-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bfe00-144">Instrukcje: Konfigurowanie powiązania WS-Metadata Exchange niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bfe00-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="bfe00-145">Instrukcje: Pobieranie metadanych przez powiązanie inne niż MEX</span><span class="sxs-lookup"><span data-stu-id="bfe00-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="bfe00-146">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="bfe00-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="bfe00-147">Metadane</span><span class="sxs-lookup"><span data-stu-id="bfe00-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bfe00-148">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bfe00-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bfe00-149">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="bfe00-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bfe00-150">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="bfe00-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bfe00-151">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="bfe00-151">\<binding></span></span>](../../../misc/binding.md)
