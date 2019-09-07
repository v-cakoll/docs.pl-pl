---
title: <behaviors>przepływu pracy
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398876"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="a82a6-102">\<> zachowań przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="a82a6-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="a82a6-103">Ten element zawiera kolekcję **serviceBehaviors** .</span><span class="sxs-lookup"><span data-stu-id="a82a6-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="a82a6-104">Każdy element w kolekcji definiuje zachowanie elementy używane przez usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a82a6-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="a82a6-105">Każdy element zachowania jest identyfikowany przez jego unikatowy atrybut **nazwy** .</span><span class="sxs-lookup"><span data-stu-id="a82a6-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
<span data-ttu-id="a82a6-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a82a6-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a82a6-107">&nbsp;&nbsp;[ **\<systemami. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="a82a6-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="a82a6-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<> zachowań**</span><span class="sxs-lookup"><span data-stu-id="a82a6-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a82a6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a82a6-109">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a82a6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a82a6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a82a6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a82a6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a82a6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a82a6-112">Attributes</span></span>  
 <span data-ttu-id="a82a6-113">Brak</span><span class="sxs-lookup"><span data-stu-id="a82a6-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a82a6-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a82a6-114">Child Elements</span></span>  
  
|<span data-ttu-id="a82a6-115">Element</span><span class="sxs-lookup"><span data-stu-id="a82a6-115">Element</span></span>|<span data-ttu-id="a82a6-116">Opis</span><span class="sxs-lookup"><span data-stu-id="a82a6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a82a6-117">\<> serviceBehaviors</span><span class="sxs-lookup"><span data-stu-id="a82a6-117">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="a82a6-118">Ta sekcja konfiguracji reprezentuje wszystkie zachowania zdefiniowanych na potrzeby usługi określonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a82a6-118">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a82a6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a82a6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="a82a6-120">Element</span><span class="sxs-lookup"><span data-stu-id="a82a6-120">Element</span></span>|<span data-ttu-id="a82a6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="a82a6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a82a6-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a82a6-122">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="a82a6-123">Element główny wszystkich elementów konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="a82a6-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a82a6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a82a6-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="a82a6-125">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="a82a6-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
