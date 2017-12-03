---
title: '&lt;limity czasu&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da80ab797078e1fe912ccbfff07d7fb2da49664e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="95fdd-102">&lt;limity czasu&gt;</span><span class="sxs-lookup"><span data-stu-id="95fdd-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="95fdd-103">Reprezentuje element konfiguracji, który określa przedział czasu dozwolony na otwarcie lub zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="95fdd-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="95fdd-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="95fdd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="95fdd-105">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="95fdd-105">\<client></span></span>  
<span data-ttu-id="95fdd-106">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="95fdd-106">\<endpoint></span></span>  
<span data-ttu-id="95fdd-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="95fdd-107">\<host></span></span>  
<span data-ttu-id="95fdd-108">\<limity czasu ></span><span class="sxs-lookup"><span data-stu-id="95fdd-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95fdd-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="95fdd-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95fdd-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95fdd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="95fdd-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95fdd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95fdd-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95fdd-112">Attributes</span></span>  
  
|<span data-ttu-id="95fdd-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95fdd-113">Attribute</span></span>|<span data-ttu-id="95fdd-114">Opis</span><span class="sxs-lookup"><span data-stu-id="95fdd-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="95fdd-115">A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla na zamknięcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="95fdd-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="95fdd-116">A <xref:System.TimeSpan> wartość, która określa okres czasu dozwolony dla na otwarcie usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="95fdd-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95fdd-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95fdd-117">Child Elements</span></span>  
 <span data-ttu-id="95fdd-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="95fdd-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95fdd-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95fdd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="95fdd-120">Element</span><span class="sxs-lookup"><span data-stu-id="95fdd-120">Element</span></span>|<span data-ttu-id="95fdd-121">Opis</span><span class="sxs-lookup"><span data-stu-id="95fdd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95fdd-122">\<host ></span><span class="sxs-lookup"><span data-stu-id="95fdd-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="95fdd-123">Element konfiguracji określa ustawienia dla usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="95fdd-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95fdd-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95fdd-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="95fdd-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="95fdd-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
