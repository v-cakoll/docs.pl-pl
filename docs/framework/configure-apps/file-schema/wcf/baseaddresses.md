---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850210"
---
# <a name="baseaddresses"></a><span data-ttu-id="d2665-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="d2665-101">\<baseAddresses></span></span>
<span data-ttu-id="d2665-102">Reprezentuje kolekcję `baseAddress` elementów, które są adresami podstawowymi dla hosta usługi w środowisku własnym.</span><span class="sxs-lookup"><span data-stu-id="d2665-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="d2665-103">W przypadku obecności adresu podstawowego punkty końcowe można skonfigurować przy użyciu adresów względnych dla adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d2665-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
<span data-ttu-id="d2665-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d2665-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d2665-105">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d2665-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d2665-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)</span><span class="sxs-lookup"><span data-stu-id="d2665-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="d2665-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi**](service.md)</span><span class="sxs-lookup"><span data-stu-id="d2665-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="d2665-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hosta**](host.md)</span><span class="sxs-lookup"><span data-stu-id="d2665-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="d2665-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<baseAddresses >**</span><span class="sxs-lookup"><span data-stu-id="d2665-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2665-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2665-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="d2665-111">Typ</span><span class="sxs-lookup"><span data-stu-id="d2665-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2665-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d2665-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d2665-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d2665-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2665-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d2665-114">Attributes</span></span>  
 <span data-ttu-id="d2665-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="d2665-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d2665-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d2665-116">Child Elements</span></span>  
  
|<span data-ttu-id="d2665-117">Element</span><span class="sxs-lookup"><span data-stu-id="d2665-117">Element</span></span>|<span data-ttu-id="d2665-118">Opis</span><span class="sxs-lookup"><span data-stu-id="d2665-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2665-119">\<add></span><span class="sxs-lookup"><span data-stu-id="d2665-119">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="d2665-120">Element konfiguracji, który określa adresy podstawowe używane przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d2665-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2665-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d2665-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d2665-122">Element</span><span class="sxs-lookup"><span data-stu-id="d2665-122">Element</span></span>|<span data-ttu-id="d2665-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d2665-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2665-124">\<host></span><span class="sxs-lookup"><span data-stu-id="d2665-124">\<host></span></span>](host.md)|<span data-ttu-id="d2665-125">Element konfiguracji, który określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="d2665-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2665-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2665-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="d2665-127">Hosting</span><span class="sxs-lookup"><span data-stu-id="d2665-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
