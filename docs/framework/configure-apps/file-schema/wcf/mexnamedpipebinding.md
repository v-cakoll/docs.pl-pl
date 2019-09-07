---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: b26201064aad3a8a09d8604a9706fe3c149cbf58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400233"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="1f200-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1f200-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="1f200-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="1f200-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="1f200-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f200-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f200-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f200-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1f200-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1f200-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1f200-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="1f200-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f200-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f200-107">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f200-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1f200-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1f200-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1f200-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f200-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1f200-110">Attributes</span></span>  
  
|<span data-ttu-id="1f200-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1f200-111">Attribute</span></span>|<span data-ttu-id="1f200-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1f200-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1f200-113"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="1f200-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1f200-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f200-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f200-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f200-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="1f200-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1f200-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1f200-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="1f200-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1f200-118">Każde powiązanie ma `name` atrybut i `namespace` , który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="1f200-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="1f200-119">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="1f200-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="1f200-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="1f200-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1f200-121">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="1f200-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1f200-122"><xref:System.TimeSpan> Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="1f200-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1f200-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f200-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f200-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f200-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1f200-125"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="1f200-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1f200-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f200-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f200-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="1f200-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1f200-128"><xref:System.TimeSpan> Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="1f200-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1f200-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="1f200-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f200-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="1f200-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f200-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1f200-131">Child Elements</span></span>  
 <span data-ttu-id="1f200-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="1f200-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f200-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1f200-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1f200-134">Element</span><span class="sxs-lookup"><span data-stu-id="1f200-134">Element</span></span>|<span data-ttu-id="1f200-135">Opis</span><span class="sxs-lookup"><span data-stu-id="1f200-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f200-136">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="1f200-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="1f200-137">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1f200-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f200-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f200-138">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="1f200-139">Instrukcje: Publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1f200-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="1f200-140">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="1f200-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="1f200-141">Metadane</span><span class="sxs-lookup"><span data-stu-id="1f200-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="1f200-142">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1f200-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f200-143">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1f200-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1f200-144">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1f200-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1f200-145">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="1f200-145">\<binding></span></span>](../../../misc/binding.md)
