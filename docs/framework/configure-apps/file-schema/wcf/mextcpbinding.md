---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 91c1d17ef450200c95d7f871e8cbee85ddd260d1
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738902"
---
# <a name="mextcpbinding"></a><span data-ttu-id="14448-101">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="14448-101">\<mexTcpBinding></span></span>
<span data-ttu-id="14448-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="14448-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="14448-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="14448-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14448-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="14448-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="14448-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="14448-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="14448-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="14448-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14448-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="14448-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14448-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="14448-108">Attributes and Elements</span></span>  
 <span data-ttu-id="14448-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="14448-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14448-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="14448-110">Attributes</span></span>  
  
|<span data-ttu-id="14448-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="14448-111">Attribute</span></span>|<span data-ttu-id="14448-112">Opis</span><span class="sxs-lookup"><span data-stu-id="14448-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="14448-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="14448-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="14448-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14448-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14448-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="14448-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="14448-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="14448-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="14448-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="14448-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="14448-118">Każde powiązanie ma atrybut `name` i `namespace`, który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="14448-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="14448-119">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="14448-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="14448-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="14448-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="14448-121">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="14448-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="14448-122">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="14448-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="14448-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14448-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14448-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="14448-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="14448-125">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="14448-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="14448-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14448-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14448-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="14448-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="14448-128">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="14448-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="14448-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14448-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14448-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="14448-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14448-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="14448-131">Child Elements</span></span>  
 <span data-ttu-id="14448-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="14448-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14448-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="14448-133">Parent Elements</span></span>  
  
|<span data-ttu-id="14448-134">Element</span><span class="sxs-lookup"><span data-stu-id="14448-134">Element</span></span>|<span data-ttu-id="14448-135">Opis</span><span class="sxs-lookup"><span data-stu-id="14448-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14448-136">> powiązań\<</span><span class="sxs-lookup"><span data-stu-id="14448-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="14448-137">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="14448-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14448-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14448-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="14448-139">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="14448-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="14448-140">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="14448-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="14448-141">Metadane</span><span class="sxs-lookup"><span data-stu-id="14448-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="14448-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="14448-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="14448-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="14448-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="14448-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="14448-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="14448-145">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="14448-145">\<binding></span></span>](bindings.md)
