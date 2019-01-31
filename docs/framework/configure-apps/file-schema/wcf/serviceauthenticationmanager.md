---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 7708dd8a572dd24c2852410b1781fce2807efab9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263488"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="99b6b-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="99b6b-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="99b6b-102">Zawiera element konfiguracji przepływu pracy, który ustanawia na poziomie usługi ważności transmisji, wiadomości i przy jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="99b6b-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="99b6b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99b6b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="99b6b-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="99b6b-104">\<behaviors></span></span>  
<span data-ttu-id="99b6b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="99b6b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="99b6b-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="99b6b-106">\<behavior></span></span>  
<span data-ttu-id="99b6b-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="99b6b-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99b6b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="99b6b-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99b6b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99b6b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99b6b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99b6b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99b6b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99b6b-111">Attributes</span></span>  
  
|<span data-ttu-id="99b6b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="99b6b-112">Attribute</span></span>|<span data-ttu-id="99b6b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="99b6b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99b6b-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="99b6b-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="99b6b-115">Ciąg, który określa typ zasady uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="99b6b-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99b6b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99b6b-116">Child Elements</span></span>  
 <span data-ttu-id="99b6b-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="99b6b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99b6b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99b6b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="99b6b-119">Element</span><span class="sxs-lookup"><span data-stu-id="99b6b-119">Element</span></span>|<span data-ttu-id="99b6b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="99b6b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99b6b-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="99b6b-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="99b6b-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="99b6b-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99b6b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99b6b-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
