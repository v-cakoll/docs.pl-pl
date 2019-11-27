---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430875"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="64eb2-101">\<mexNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="64eb2-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="64eb2-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="64eb2-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="64eb2-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="64eb2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="64eb2-104">&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="64eb2-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="64eb2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="64eb2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="64eb2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="64eb2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64eb2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="64eb2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64eb2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="64eb2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="64eb2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="64eb2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64eb2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="64eb2-110">Attributes</span></span>  
  
|<span data-ttu-id="64eb2-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="64eb2-111">Attribute</span></span>|<span data-ttu-id="64eb2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="64eb2-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="64eb2-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="64eb2-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="64eb2-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="64eb2-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="64eb2-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="64eb2-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="64eb2-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="64eb2-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="64eb2-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="64eb2-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="64eb2-118">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="64eb2-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="64eb2-119">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="64eb2-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="64eb2-120">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="64eb2-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="64eb2-121">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="64eb2-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="64eb2-122">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="64eb2-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="64eb2-123">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="64eb2-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="64eb2-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="64eb2-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="64eb2-125">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="64eb2-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="64eb2-126">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="64eb2-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="64eb2-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="64eb2-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="64eb2-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="64eb2-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="64eb2-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="64eb2-129">Child Elements</span></span>  
 <span data-ttu-id="64eb2-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="64eb2-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="64eb2-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="64eb2-131">Parent Elements</span></span>  
  
|<span data-ttu-id="64eb2-132">Element</span><span class="sxs-lookup"><span data-stu-id="64eb2-132">Element</span></span>|<span data-ttu-id="64eb2-133">Opis</span><span class="sxs-lookup"><span data-stu-id="64eb2-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="64eb2-134">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="64eb2-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="64eb2-135">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="64eb2-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="64eb2-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64eb2-136">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="64eb2-137">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="64eb2-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="64eb2-138">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="64eb2-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="64eb2-139">Metadane</span><span class="sxs-lookup"><span data-stu-id="64eb2-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="64eb2-140">Powiązania</span><span class="sxs-lookup"><span data-stu-id="64eb2-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="64eb2-141">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="64eb2-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="64eb2-142">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="64eb2-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="64eb2-143">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="64eb2-143">\<binding></span></span>](bindings.md)
