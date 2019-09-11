---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b9c67ac03f0eb73a2a4cdd43ab48fe12871a1cc3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854965"
---
# <a name="timeouts"></a><span data-ttu-id="098c3-101">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="098c3-101">\<timeOuts></span></span>
<span data-ttu-id="098c3-102">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="098c3-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
<span data-ttu-id="098c3-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="098c3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="098c3-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="098c3-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="098c3-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usług**](services.md)</span><span class="sxs-lookup"><span data-stu-id="098c3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="098c3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> usługi**](service.md)</span><span class="sxs-lookup"><span data-stu-id="098c3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="098c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> hosta**](host.md)</span><span class="sxs-lookup"><span data-stu-id="098c3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="098c3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Limity czasu >**</span><span class="sxs-lookup"><span data-stu-id="098c3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<timeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098c3-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="098c3-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="098c3-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="098c3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="098c3-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="098c3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="098c3-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="098c3-112">Attributes</span></span>  
  
|<span data-ttu-id="098c3-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="098c3-113">Attribute</span></span>|<span data-ttu-id="098c3-114">Opis</span><span class="sxs-lookup"><span data-stu-id="098c3-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="098c3-115"><xref:System.TimeSpan> Wartość, która określa przedział czasu, jaki może być zamknięty dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="098c3-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="098c3-116"><xref:System.TimeSpan> Wartość, która określa przedział czasu, jaki może otworzyć Host usługi.</span><span class="sxs-lookup"><span data-stu-id="098c3-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="098c3-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="098c3-117">Child Elements</span></span>  
 <span data-ttu-id="098c3-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="098c3-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="098c3-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="098c3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="098c3-120">Element</span><span class="sxs-lookup"><span data-stu-id="098c3-120">Element</span></span>|<span data-ttu-id="098c3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="098c3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="098c3-122">\<host></span><span class="sxs-lookup"><span data-stu-id="098c3-122">\<host></span></span>](host.md)|<span data-ttu-id="098c3-123">Element konfiguracji, który określa ustawienia dla hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="098c3-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="098c3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="098c3-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="098c3-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="098c3-125">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
