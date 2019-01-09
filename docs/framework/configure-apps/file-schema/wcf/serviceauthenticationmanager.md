---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3456ffa952372b014d579b5c420f7c44222fdad5
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145357"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="d3e43-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="d3e43-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="d3e43-103">Zawiera element konfiguracji przepływu pracy, który ustanawia na poziomie usługi ważności transmisji, wiadomości i przy jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="d3e43-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="d3e43-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d3e43-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d3e43-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="d3e43-105">\<behaviors></span></span>  
<span data-ttu-id="d3e43-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d3e43-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d3e43-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d3e43-107">\<behavior></span></span>  
<span data-ttu-id="d3e43-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="d3e43-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e43-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3e43-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3e43-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d3e43-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3e43-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d3e43-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3e43-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d3e43-112">Attributes</span></span>  
  
|<span data-ttu-id="d3e43-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d3e43-113">Attribute</span></span>|<span data-ttu-id="d3e43-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d3e43-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3e43-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="d3e43-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="d3e43-116">Ciąg, który określa typ zasady uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="d3e43-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3e43-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d3e43-117">Child Elements</span></span>  
 <span data-ttu-id="d3e43-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="d3e43-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3e43-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d3e43-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d3e43-120">Element</span><span class="sxs-lookup"><span data-stu-id="d3e43-120">Element</span></span>|<span data-ttu-id="d3e43-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d3e43-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3e43-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="d3e43-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d3e43-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="d3e43-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3e43-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3e43-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
