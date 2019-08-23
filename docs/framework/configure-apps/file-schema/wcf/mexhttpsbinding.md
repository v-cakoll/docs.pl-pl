---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 30d1aa27ce29b6aa4091c3e7be05746ad462102a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931270"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="bacb6-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="bacb6-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="bacb6-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="bacb6-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="bacb6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bacb6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="bacb6-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="bacb6-104">\<bindings></span></span>  
<span data-ttu-id="bacb6-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="bacb6-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bacb6-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bacb6-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bacb6-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bacb6-107">Attributes and Elements</span></span>  
 <span data-ttu-id="bacb6-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bacb6-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bacb6-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bacb6-109">Attributes</span></span>  
  
|<span data-ttu-id="bacb6-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bacb6-110">Attribute</span></span>|<span data-ttu-id="bacb6-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bacb6-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bacb6-112"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="bacb6-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bacb6-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bacb6-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bacb6-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bacb6-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bacb6-115">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="bacb6-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bacb6-116">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="bacb6-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bacb6-117">Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="bacb6-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="bacb6-118">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="bacb6-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="bacb6-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="bacb6-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bacb6-120">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bacb6-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bacb6-121"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="bacb6-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bacb6-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bacb6-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bacb6-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bacb6-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bacb6-124"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="bacb6-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bacb6-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bacb6-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bacb6-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bacb6-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bacb6-127"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="bacb6-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bacb6-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bacb6-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bacb6-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bacb6-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bacb6-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bacb6-130">Child Elements</span></span>  
 <span data-ttu-id="bacb6-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="bacb6-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bacb6-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bacb6-132">Parent Elements</span></span>  
  
|<span data-ttu-id="bacb6-133">Element</span><span class="sxs-lookup"><span data-stu-id="bacb6-133">Element</span></span>|<span data-ttu-id="bacb6-134">Opis</span><span class="sxs-lookup"><span data-stu-id="bacb6-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bacb6-135">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="bacb6-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bacb6-136">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="bacb6-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bacb6-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bacb6-137">Remarks</span></span>  
 <span data-ttu-id="bacb6-138">To powiązanie jest zasadniczo `WSHttpBinding` powiązaniem, które obsługuje zabezpieczenia na poziomie transportu przy użyciu certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="bacb6-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="bacb6-139">Aby uzyskać więcej informacji o konfigurowaniu i używaniu takiego punktu końcowego [metadanych, zobacz How to: Skonfiguruj niestandardowe powiązanie](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)WS-Metadata Exchange, [jak: Pobieranie metadanych za pośrednictwem powiązania](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)niezwiązanego z elementem MEX i przykładowym, niestandardowym bezpiecznym [punktem końcowym metadanych](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="bacb6-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bacb6-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bacb6-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="bacb6-141">Instrukcje: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bacb6-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bacb6-142">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bacb6-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bacb6-143">Instrukcje: Konfigurowanie powiązania WS-Metadata Exchange niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bacb6-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="bacb6-144">Instrukcje: Pobieranie metadanych przez powiązanie inne niż MEX</span><span class="sxs-lookup"><span data-stu-id="bacb6-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="bacb6-145">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="bacb6-145">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="bacb6-146">Metadane</span><span class="sxs-lookup"><span data-stu-id="bacb6-146">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bacb6-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bacb6-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bacb6-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="bacb6-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bacb6-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="bacb6-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bacb6-150">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="bacb6-150">\<binding></span></span>](../../../misc/binding.md)
