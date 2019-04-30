---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670381"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="cee88-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="cee88-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="cee88-102">Zawiera element konfiguracji przepływu pracy, który ustanawia na poziomie usługi ważności transmisji, wiadomości i przy jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="cee88-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="cee88-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cee88-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="cee88-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="cee88-104">\<behaviors></span></span>  
<span data-ttu-id="cee88-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cee88-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="cee88-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cee88-106">\<behavior></span></span>  
<span data-ttu-id="cee88-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="cee88-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cee88-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cee88-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cee88-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cee88-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cee88-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cee88-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cee88-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cee88-111">Attributes</span></span>  
  
|<span data-ttu-id="cee88-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cee88-112">Attribute</span></span>|<span data-ttu-id="cee88-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cee88-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cee88-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="cee88-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="cee88-115">Ciąg, który określa typ zasady uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="cee88-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cee88-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cee88-116">Child Elements</span></span>  
 <span data-ttu-id="cee88-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="cee88-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cee88-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cee88-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cee88-119">Element</span><span class="sxs-lookup"><span data-stu-id="cee88-119">Element</span></span>|<span data-ttu-id="cee88-120">Opis</span><span class="sxs-lookup"><span data-stu-id="cee88-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cee88-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="cee88-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="cee88-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="cee88-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cee88-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cee88-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
