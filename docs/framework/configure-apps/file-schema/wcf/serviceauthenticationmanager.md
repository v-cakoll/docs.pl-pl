---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3b58214a1fd7a50fb1a9ab3dfee0a14870f8a476
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="5a8e6-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="5a8e6-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="5a8e6-103">Udostępnia element konfiguracji przepływu pracy, który ustanawia na poziomie usługi prawidłowości transmisji, wiadomości lub nadawca...</span><span class="sxs-lookup"><span data-stu-id="5a8e6-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="5a8e6-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5a8e6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a8e6-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="5a8e6-105">\<behaviors></span></span>  
<span data-ttu-id="5a8e6-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5a8e6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5a8e6-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5a8e6-107">\<behavior></span></span>  
<span data-ttu-id="5a8e6-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="5a8e6-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8e6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a8e6-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a8e6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5a8e6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a8e6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5a8e6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a8e6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5a8e6-112">Attributes</span></span>  
  
|<span data-ttu-id="5a8e6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5a8e6-113">Attribute</span></span>|<span data-ttu-id="5a8e6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="5a8e6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a8e6-115">serviceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="5a8e6-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="5a8e6-116">Ciąg określający typ zasad uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="5a8e6-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a8e6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5a8e6-117">Child Elements</span></span>  
 <span data-ttu-id="5a8e6-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="5a8e6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a8e6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5a8e6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5a8e6-120">Element</span><span class="sxs-lookup"><span data-stu-id="5a8e6-120">Element</span></span>|<span data-ttu-id="5a8e6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="5a8e6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a8e6-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="5a8e6-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="5a8e6-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="5a8e6-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a8e6-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a8e6-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
