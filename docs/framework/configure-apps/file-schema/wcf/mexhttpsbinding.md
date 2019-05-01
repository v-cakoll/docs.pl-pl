---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 4e96c28ac9b372092d06538d24d165dde6c5fe48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772544"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="4a08b-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="4a08b-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="4a08b-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a08b-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="4a08b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a08b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a08b-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4a08b-104">\<bindings></span></span>  
<span data-ttu-id="4a08b-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="4a08b-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a08b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a08b-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a08b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a08b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="4a08b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a08b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a08b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a08b-109">Attributes</span></span>  
  
|<span data-ttu-id="4a08b-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a08b-110">Attribute</span></span>|<span data-ttu-id="4a08b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4a08b-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4a08b-112">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="4a08b-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4a08b-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4a08b-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4a08b-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4a08b-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="4a08b-115">Ciąg, który zawiera nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="4a08b-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4a08b-116">Wartość ta powinna być unikatowy, ponieważ jest używany jako identyfikator dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="4a08b-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4a08b-117">Każde powiązanie ma `name` i `namespace` atrybutu, razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="4a08b-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="4a08b-118">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="4a08b-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="4a08b-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="4a08b-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4a08b-120">Aby uzyskać więcej informacji o domyślnej konfiguracji i powiązania pustego oraz zachowań, zobacz [uproszczona konfiguracja](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4a08b-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="4a08b-121">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="4a08b-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4a08b-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4a08b-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4a08b-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4a08b-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4a08b-124">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="4a08b-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4a08b-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4a08b-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4a08b-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4a08b-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4a08b-127">A <xref:System.TimeSpan> wartość, która określa przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="4a08b-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4a08b-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4a08b-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4a08b-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4a08b-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a08b-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a08b-130">Child Elements</span></span>  
 <span data-ttu-id="4a08b-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="4a08b-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a08b-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a08b-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4a08b-133">Element</span><span class="sxs-lookup"><span data-stu-id="4a08b-133">Element</span></span>|<span data-ttu-id="4a08b-134">Opis</span><span class="sxs-lookup"><span data-stu-id="4a08b-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a08b-135">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4a08b-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="4a08b-136">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4a08b-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a08b-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a08b-137">Remarks</span></span>  
 <span data-ttu-id="4a08b-138">To powiązanie jest zasadniczo `WSHttpBinding` powiązania, który obsługuje zabezpieczenia na poziomie transportu za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="4a08b-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="4a08b-139">Aby uzyskać więcej informacji na temat konfigurowania i korzystania z punktu końcowego metadanych, zobacz [jak: Konfigurowanie niestandardowego protokołu WS-Metadata Exchange powiązania](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [jak: Pobieranie metadanych przez MEX powiązanie inne niż](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), a przykład [niestandardowy bezpieczny punkt końcowy metadanych](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="4a08b-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a08b-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a08b-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="4a08b-141">Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4a08b-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="4a08b-142">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="4a08b-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="4a08b-143">Instrukcje: Konfigurowanie niestandardowego protokołu WS-Metadata Exchange powiązania</span><span class="sxs-lookup"><span data-stu-id="4a08b-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="4a08b-144">Instrukcje: Pobieranie metadanych przez MEX powiązanie inne niż</span><span class="sxs-lookup"><span data-stu-id="4a08b-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="4a08b-145">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="4a08b-145">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="4a08b-146">Metadane</span><span class="sxs-lookup"><span data-stu-id="4a08b-146">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="4a08b-147">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4a08b-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="4a08b-148">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4a08b-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4a08b-149">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4a08b-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4a08b-150">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4a08b-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
