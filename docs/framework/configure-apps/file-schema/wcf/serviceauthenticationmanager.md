---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936412"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="0a78b-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="0a78b-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="0a78b-102">Zawiera element konfiguracji przepływu pracy, który ustala na poziomie usługi ważność transmisji, wiadomości lub nadawcy.</span><span class="sxs-lookup"><span data-stu-id="0a78b-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="0a78b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0a78b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a78b-104">\<> zachowań</span><span class="sxs-lookup"><span data-stu-id="0a78b-104">\<behaviors></span></span>  
<span data-ttu-id="0a78b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0a78b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0a78b-106">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="0a78b-106">\<behavior></span></span>  
<span data-ttu-id="0a78b-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="0a78b-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a78b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a78b-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a78b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0a78b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0a78b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0a78b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a78b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0a78b-111">Attributes</span></span>  
  
|<span data-ttu-id="0a78b-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0a78b-112">Attribute</span></span>|<span data-ttu-id="0a78b-113">Opis</span><span class="sxs-lookup"><span data-stu-id="0a78b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a78b-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="0a78b-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="0a78b-115">Ciąg określający typ zasad uwierzytelniania dla bieżącego zachowania.</span><span class="sxs-lookup"><span data-stu-id="0a78b-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a78b-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0a78b-116">Child Elements</span></span>  
 <span data-ttu-id="0a78b-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="0a78b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a78b-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0a78b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0a78b-119">Element</span><span class="sxs-lookup"><span data-stu-id="0a78b-119">Element</span></span>|<span data-ttu-id="0a78b-120">Opis</span><span class="sxs-lookup"><span data-stu-id="0a78b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a78b-121">\<> zachowania</span><span class="sxs-lookup"><span data-stu-id="0a78b-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="0a78b-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="0a78b-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a78b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a78b-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
