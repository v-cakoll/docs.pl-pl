---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8a8145bbfcb3eefb06d159d834232d94166fa6dd
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736719"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="02d18-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="02d18-101">\<mexHttpBinding></span></span>
<span data-ttu-id="02d18-102">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="02d18-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="02d18-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="02d18-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="02d18-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="02d18-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="02d18-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="02d18-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="02d18-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="02d18-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d18-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="02d18-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02d18-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="02d18-108">Attributes and Elements</span></span>  
 <span data-ttu-id="02d18-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="02d18-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02d18-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="02d18-110">Attributes</span></span>  
  
|<span data-ttu-id="02d18-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="02d18-111">Attribute</span></span>|<span data-ttu-id="02d18-112">Opis</span><span class="sxs-lookup"><span data-stu-id="02d18-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="02d18-113">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="02d18-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="02d18-114">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="02d18-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02d18-115">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="02d18-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="02d18-116">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="02d18-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="02d18-117">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="02d18-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="02d18-118">Każde powiązanie ma atrybut `name` i `namespace`, który jednoznacznie identyfikuje go w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="02d18-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="02d18-119">Ponadto ta nazwa jest unikatowa wśród powiązań tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="02d18-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="02d18-120">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="02d18-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="02d18-121">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="02d18-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="02d18-122">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji otwierania.</span><span class="sxs-lookup"><span data-stu-id="02d18-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="02d18-123">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="02d18-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02d18-124">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="02d18-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="02d18-125">Wartość <xref:System.TimeSpan>, która określa przedział czasu podanego na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="02d18-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="02d18-126">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="02d18-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02d18-127">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="02d18-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="02d18-128">Wartość <xref:System.TimeSpan>, która określa interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="02d18-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="02d18-129">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="02d18-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="02d18-130">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="02d18-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02d18-131">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="02d18-131">Child Elements</span></span>  
 <span data-ttu-id="02d18-132">Brak.</span><span class="sxs-lookup"><span data-stu-id="02d18-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02d18-133">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="02d18-133">Parent Elements</span></span>  
  
|<span data-ttu-id="02d18-134">Element</span><span class="sxs-lookup"><span data-stu-id="02d18-134">Element</span></span>|<span data-ttu-id="02d18-135">Opis</span><span class="sxs-lookup"><span data-stu-id="02d18-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02d18-136">> powiązań\<</span><span class="sxs-lookup"><span data-stu-id="02d18-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="02d18-137">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="02d18-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02d18-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02d18-138">Remarks</span></span>  
 <span data-ttu-id="02d18-139">To powiązanie jest zasadniczo `WSHttpBinding` powiązań z wyłączonymi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="02d18-139">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="02d18-140">Obsługuje większość żądań metadanych.</span><span class="sxs-lookup"><span data-stu-id="02d18-140">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02d18-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02d18-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="02d18-142">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="02d18-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="02d18-143">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="02d18-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="02d18-144">Metadane</span><span class="sxs-lookup"><span data-stu-id="02d18-144">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="02d18-145">Powiązania</span><span class="sxs-lookup"><span data-stu-id="02d18-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="02d18-146">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="02d18-146">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="02d18-147">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="02d18-147">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="02d18-148">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="02d18-148">\<binding></span></span>](bindings.md)
