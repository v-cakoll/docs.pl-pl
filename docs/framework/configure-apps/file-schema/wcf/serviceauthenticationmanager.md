---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: fd04b10c0ac0bef4087daa1012a1b8bd3a5880e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493641"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="87dd4-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="87dd4-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="87dd4-103">Zawiera element konfiguracji przepływu pracy, który ustanawia na poziomie usługi ważności transmisji, wiadomości i przy jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="87dd4-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="87dd4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="87dd4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="87dd4-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="87dd4-105">\<behaviors></span></span>  
<span data-ttu-id="87dd4-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="87dd4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="87dd4-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="87dd4-107">\<behavior></span></span>  
<span data-ttu-id="87dd4-108">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="87dd4-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87dd4-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="87dd4-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87dd4-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="87dd4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87dd4-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="87dd4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87dd4-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="87dd4-112">Attributes</span></span>  
  
|<span data-ttu-id="87dd4-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="87dd4-113">Attribute</span></span>|<span data-ttu-id="87dd4-114">Opis</span><span class="sxs-lookup"><span data-stu-id="87dd4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87dd4-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="87dd4-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="87dd4-116">Ciąg, który określa typ zasady uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="87dd4-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87dd4-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="87dd4-117">Child Elements</span></span>  
 <span data-ttu-id="87dd4-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="87dd4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87dd4-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="87dd4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="87dd4-120">Element</span><span class="sxs-lookup"><span data-stu-id="87dd4-120">Element</span></span>|<span data-ttu-id="87dd4-121">Opis</span><span class="sxs-lookup"><span data-stu-id="87dd4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87dd4-122">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="87dd4-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="87dd4-123">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="87dd4-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87dd4-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87dd4-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
