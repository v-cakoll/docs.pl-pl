---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430307"
---
# <a name="mextcpbinding"></a><span data-ttu-id="bcf63-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="bcf63-101">\<mexTcpBinding></span></span>
<span data-ttu-id="bcf63-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span><span class="sxs-lookup"><span data-stu-id="bcf63-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="bcf63-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bcf63-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bcf63-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bcf63-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bcf63-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="bcf63-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="bcf63-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding>**</span><span class="sxs-lookup"><span data-stu-id="bcf63-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcf63-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="bcf63-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcf63-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bcf63-108">Attributes and Elements</span></span>  
 <span data-ttu-id="bcf63-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bcf63-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcf63-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bcf63-110">Attributes</span></span>  
  
|<span data-ttu-id="bcf63-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bcf63-111">Attribute</span></span>|<span data-ttu-id="bcf63-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bcf63-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bcf63-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bcf63-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="bcf63-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcf63-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcf63-115">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bcf63-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="bcf63-116">A string that contains the configuration name of the binding.</span><span class="sxs-lookup"><span data-stu-id="bcf63-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="bcf63-117">This value should be unique because it is used as an identification for the binding.</span><span class="sxs-lookup"><span data-stu-id="bcf63-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="bcf63-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="bcf63-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bcf63-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bcf63-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="bcf63-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bcf63-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="bcf63-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcf63-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcf63-122">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bcf63-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="bcf63-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bcf63-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="bcf63-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcf63-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcf63-125">The default is 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="bcf63-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="bcf63-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span><span class="sxs-lookup"><span data-stu-id="bcf63-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="bcf63-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="bcf63-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="bcf63-128">The default is 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="bcf63-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcf63-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bcf63-129">Child Elements</span></span>  
 <span data-ttu-id="bcf63-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="bcf63-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcf63-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bcf63-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bcf63-132">Element</span><span class="sxs-lookup"><span data-stu-id="bcf63-132">Element</span></span>|<span data-ttu-id="bcf63-133">Opis</span><span class="sxs-lookup"><span data-stu-id="bcf63-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bcf63-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="bcf63-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="bcf63-135">This element holds a collection of standard and custom bindings.</span><span class="sxs-lookup"><span data-stu-id="bcf63-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bcf63-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bcf63-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="bcf63-137">Instrukcje: publikowanie metadanych dla usługi za pomocą pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="bcf63-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="bcf63-138">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="bcf63-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="bcf63-139">Metadane</span><span class="sxs-lookup"><span data-stu-id="bcf63-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="bcf63-140">Powiązania</span><span class="sxs-lookup"><span data-stu-id="bcf63-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bcf63-141">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="bcf63-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="bcf63-142">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="bcf63-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="bcf63-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="bcf63-143">\<binding></span></span>](bindings.md)
