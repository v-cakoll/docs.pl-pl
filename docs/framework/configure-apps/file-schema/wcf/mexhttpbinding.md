---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430910"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="dac99-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="dac99-101">\<mexHttpBinding></span></span>
<span data-ttu-id="dac99-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="dac99-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="dac99-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dac99-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dac99-104">&nbsp;&nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="dac99-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dac99-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="dac99-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dac99-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="dac99-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac99-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="dac99-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dac99-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dac99-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dac99-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dac99-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dac99-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dac99-110">Attributes</span></span>  
  
|<span data-ttu-id="dac99-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="dac99-111">Attribute</span></span>|<span data-ttu-id="dac99-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dac99-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="dac99-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="dac99-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dac99-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dac99-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dac99-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dac99-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="dac99-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="dac99-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dac99-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="dac99-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="dac99-118">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="dac99-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dac99-119">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dac99-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="dac99-120">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="dac99-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dac99-121">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dac99-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dac99-122">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dac99-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="dac99-123">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="dac99-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dac99-124">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dac99-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dac99-125">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dac99-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="dac99-126">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="dac99-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dac99-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dac99-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dac99-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dac99-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dac99-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dac99-129">Child Elements</span></span>  
 <span data-ttu-id="dac99-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="dac99-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dac99-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dac99-131">Parent Elements</span></span>  
  
|<span data-ttu-id="dac99-132">Element</span><span class="sxs-lookup"><span data-stu-id="dac99-132">Element</span></span>|<span data-ttu-id="dac99-133">Opis</span><span class="sxs-lookup"><span data-stu-id="dac99-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dac99-134">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="dac99-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="dac99-135">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="dac99-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dac99-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dac99-136">Remarks</span></span>  
 <span data-ttu-id="dac99-137">To powiązanie jest zasadniczo `WSHttpBinding` powiązań z wyłączonymi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="dac99-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="dac99-138">Obsługuje większość żądań metadanych.</span><span class="sxs-lookup"><span data-stu-id="dac99-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dac99-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dac99-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="dac99-140">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dac99-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="dac99-141">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="dac99-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="dac99-142">Metadane</span><span class="sxs-lookup"><span data-stu-id="dac99-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="dac99-143">Powiązania</span><span class="sxs-lookup"><span data-stu-id="dac99-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dac99-144">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="dac99-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dac99-145">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="dac99-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dac99-146">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="dac99-146">\<binding></span></span>](bindings.md)
