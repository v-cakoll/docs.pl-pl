---
title: '&lt;Typ oświadczenia&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084218"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="a31f9-102">&lt;Typ oświadczenia&gt;</span><span class="sxs-lookup"><span data-stu-id="a31f9-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="a31f9-103">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="a31f9-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="a31f9-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a31f9-104">\<system.identityModel></span></span>  
<span data-ttu-id="a31f9-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a31f9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a31f9-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="a31f9-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="a31f9-107">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="a31f9-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a31f9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a31f9-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a31f9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a31f9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a31f9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a31f9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a31f9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a31f9-111">Attributes</span></span>  
  
|<span data-ttu-id="a31f9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a31f9-112">Attribute</span></span>|<span data-ttu-id="a31f9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a31f9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a31f9-114">— typ</span><span class="sxs-lookup"><span data-stu-id="a31f9-114">type</span></span>|<span data-ttu-id="a31f9-115">Typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="a31f9-115">The claim type.</span></span> <span data-ttu-id="a31f9-116">Zazwyczaj identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="a31f9-116">Typically a URI.</span></span> <span data-ttu-id="a31f9-117">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="a31f9-117">Required.</span></span>|  
|<span data-ttu-id="a31f9-118">optional</span><span class="sxs-lookup"><span data-stu-id="a31f9-118">optional</span></span>|<span data-ttu-id="a31f9-119">Wartość logiczna określająca, czy typ oświadczenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a31f9-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="a31f9-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a31f9-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a31f9-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a31f9-121">Child Elements</span></span>  
 <span data-ttu-id="a31f9-122">Brak</span><span class="sxs-lookup"><span data-stu-id="a31f9-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a31f9-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a31f9-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a31f9-124">Element</span><span class="sxs-lookup"><span data-stu-id="a31f9-124">Element</span></span>|<span data-ttu-id="a31f9-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a31f9-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a31f9-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="a31f9-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="a31f9-127">Określa zestaw wymagane oświadczenia przychodzące tokeny zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a31f9-127">Specifies the set of required claims for incoming security tokens.</span></span>|
