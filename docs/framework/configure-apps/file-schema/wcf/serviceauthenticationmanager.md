---
title: '&lt;serviceAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 077878ae1746008532c3bee6b12913f98afc343f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="459cb-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="459cb-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="459cb-103">Udostępnia element konfiguracji przepływu pracy, który ustanawia na poziomie usługi prawidłowości transmisji, wiadomości lub nadawca...</span><span class="sxs-lookup"><span data-stu-id="459cb-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="459cb-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="459cb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="459cb-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="459cb-105">\<behaviors></span></span>  
<span data-ttu-id="459cb-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="459cb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="459cb-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="459cb-107">\<behavior></span></span>  
<span data-ttu-id="459cb-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="459cb-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="459cb-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="459cb-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="459cb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="459cb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="459cb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="459cb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="459cb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="459cb-112">Attributes</span></span>  
  
|<span data-ttu-id="459cb-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="459cb-113">Attribute</span></span>|<span data-ttu-id="459cb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="459cb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="459cb-115">serviceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="459cb-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="459cb-116">Ciąg określający typ zasad uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="459cb-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="459cb-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="459cb-117">Child Elements</span></span>  
 <span data-ttu-id="459cb-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="459cb-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="459cb-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="459cb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="459cb-120">Element</span><span class="sxs-lookup"><span data-stu-id="459cb-120">Element</span></span>|<span data-ttu-id="459cb-121">Opis</span><span class="sxs-lookup"><span data-stu-id="459cb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="459cb-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="459cb-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="459cb-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="459cb-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="459cb-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="459cb-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
