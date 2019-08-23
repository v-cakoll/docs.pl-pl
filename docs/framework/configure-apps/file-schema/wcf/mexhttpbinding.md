---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: bb9e1fc0b3ec62c824864a74efb64c34d2076e66
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931296"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="39611-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="39611-101">\<mexHttpBinding></span></span>
<span data-ttu-id="39611-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="39611-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="39611-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39611-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="39611-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="39611-104">\<bindings></span></span>  
<span data-ttu-id="39611-105">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="39611-105">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39611-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="39611-106">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39611-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="39611-107">Attributes and Elements</span></span>  
 <span data-ttu-id="39611-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="39611-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39611-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="39611-109">Attributes</span></span>  
  
|<span data-ttu-id="39611-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="39611-110">Attribute</span></span>|<span data-ttu-id="39611-111">Opis</span><span class="sxs-lookup"><span data-stu-id="39611-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="39611-112"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="39611-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="39611-113">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39611-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39611-114">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39611-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="39611-115">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="39611-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="39611-116">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="39611-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="39611-117">Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="39611-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="39611-118">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="39611-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="39611-119">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="39611-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="39611-120">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="39611-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="39611-121"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="39611-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="39611-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39611-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39611-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39611-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="39611-124"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="39611-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="39611-125">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39611-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39611-126">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="39611-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="39611-127"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="39611-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="39611-128">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="39611-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="39611-129">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="39611-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39611-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="39611-130">Child Elements</span></span>  
 <span data-ttu-id="39611-131">Brak.</span><span class="sxs-lookup"><span data-stu-id="39611-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39611-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="39611-132">Parent Elements</span></span>  
  
|<span data-ttu-id="39611-133">Element</span><span class="sxs-lookup"><span data-stu-id="39611-133">Element</span></span>|<span data-ttu-id="39611-134">Opis</span><span class="sxs-lookup"><span data-stu-id="39611-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39611-135">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="39611-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="39611-136">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="39611-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39611-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39611-137">Remarks</span></span>  
 <span data-ttu-id="39611-138">To powiązanie jest w zasadzie `WSHttpBinding` powiązanie z wyłączonymi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="39611-138">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="39611-139">Obsługuje większość żądań metadanych.</span><span class="sxs-lookup"><span data-stu-id="39611-139">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39611-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39611-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="39611-141">Instrukcje: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="39611-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="39611-142">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="39611-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="39611-143">Metadane</span><span class="sxs-lookup"><span data-stu-id="39611-143">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="39611-144">Powiązania</span><span class="sxs-lookup"><span data-stu-id="39611-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="39611-145">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="39611-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="39611-146">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="39611-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="39611-147">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="39611-147">\<binding></span></span>](../../../misc/binding.md)
