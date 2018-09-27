---
title: '&lt;Typ oświadczenia&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47234965"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="26a55-102">&lt;Typ oświadczenia&gt;</span><span class="sxs-lookup"><span data-stu-id="26a55-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="26a55-103">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="26a55-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="26a55-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="26a55-104">\<system.identityModel></span></span>  
<span data-ttu-id="26a55-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="26a55-105">\<identityConfiguration></span></span>  
<span data-ttu-id="26a55-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="26a55-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="26a55-107">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="26a55-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26a55-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="26a55-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26a55-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="26a55-109">Attributes and Elements</span></span>  
 <span data-ttu-id="26a55-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="26a55-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26a55-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26a55-111">Attributes</span></span>  
  
|<span data-ttu-id="26a55-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="26a55-112">Attribute</span></span>|<span data-ttu-id="26a55-113">Opis</span><span class="sxs-lookup"><span data-stu-id="26a55-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26a55-114">— typ</span><span class="sxs-lookup"><span data-stu-id="26a55-114">type</span></span>|<span data-ttu-id="26a55-115">Typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="26a55-115">The claim type.</span></span> <span data-ttu-id="26a55-116">Zazwyczaj identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="26a55-116">Typically a URI.</span></span> <span data-ttu-id="26a55-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="26a55-117">Required.</span></span>|  
|<span data-ttu-id="26a55-118">optional</span><span class="sxs-lookup"><span data-stu-id="26a55-118">optional</span></span>|<span data-ttu-id="26a55-119">Wartość logiczna określająca, czy typ oświadczenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="26a55-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="26a55-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="26a55-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="26a55-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="26a55-121">Child Elements</span></span>  
 <span data-ttu-id="26a55-122">Brak</span><span class="sxs-lookup"><span data-stu-id="26a55-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26a55-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="26a55-123">Parent Elements</span></span>  
  
|<span data-ttu-id="26a55-124">Element</span><span class="sxs-lookup"><span data-stu-id="26a55-124">Element</span></span>|<span data-ttu-id="26a55-125">Opis</span><span class="sxs-lookup"><span data-stu-id="26a55-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26a55-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="26a55-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="26a55-127">Określa zestaw wymagane oświadczenia przychodzące tokeny zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="26a55-127">Specifies the set of required claims for incoming security tokens.</span></span>|
