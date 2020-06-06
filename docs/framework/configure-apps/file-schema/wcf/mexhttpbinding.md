---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430910"
---
# \<mexHttpBinding>
<span data-ttu-id="90560-101">Określa ustawienia dla powiązania używanego w wymianie wiadomości WS-MetadataExchange (WS-MEX) za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="90560-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="90560-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="90560-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90560-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="90560-103">Attributes and Elements</span></span>  
 <span data-ttu-id="90560-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="90560-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90560-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="90560-105">Attributes</span></span>  
  
|<span data-ttu-id="90560-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="90560-106">Attribute</span></span>|<span data-ttu-id="90560-107">Opis</span><span class="sxs-lookup"><span data-stu-id="90560-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="90560-108"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="90560-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="90560-109">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="90560-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="90560-110">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="90560-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="90560-111">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="90560-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="90560-112">Ta wartość powinna być unikatowa, ponieważ jest używana jako identyfikacja dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="90560-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="90560-113">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="90560-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="90560-114">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="90560-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="90560-115"><xref:System.TimeSpan>Wartość, która określa przedział czasu podanego na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="90560-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="90560-116">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="90560-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="90560-117">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="90560-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="90560-118">Wartość określająca <xref:System.TimeSpan> interwał czasu podanego do ukończenia operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="90560-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="90560-119">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="90560-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="90560-120">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="90560-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="90560-121"><xref:System.TimeSpan>Wartość określająca interwał czasu podanego do ukończenia operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="90560-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="90560-122">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="90560-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="90560-123">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="90560-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90560-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="90560-124">Child Elements</span></span>  
 <span data-ttu-id="90560-125">Brak.</span><span class="sxs-lookup"><span data-stu-id="90560-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90560-126">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="90560-126">Parent Elements</span></span>  
  
|<span data-ttu-id="90560-127">Element</span><span class="sxs-lookup"><span data-stu-id="90560-127">Element</span></span>|<span data-ttu-id="90560-128">Opis</span><span class="sxs-lookup"><span data-stu-id="90560-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="90560-129">Ten element zawiera kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="90560-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90560-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90560-130">Remarks</span></span>  
 <span data-ttu-id="90560-131">To powiązanie jest w zasadzie `WSHttpBinding` powiązanie z wyłączonymi zabezpieczeniami.</span><span class="sxs-lookup"><span data-stu-id="90560-131">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="90560-132">Obsługuje większość żądań metadanych.</span><span class="sxs-lookup"><span data-stu-id="90560-132">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90560-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90560-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="90560-134">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="90560-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="90560-135">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="90560-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="90560-136">Metadane</span><span class="sxs-lookup"><span data-stu-id="90560-136">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="90560-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="90560-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="90560-138">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="90560-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="90560-139">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="90560-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
