---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 4253aec961b812b6893ee201861d2ab38048032a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942880"
---
# <a name="claimtype"></a><span data-ttu-id="700e2-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="700e2-101">\<claimType></span></span>
<span data-ttu-id="700e2-102">Określa jedno opcjonalne lub wymagane żądanie dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="700e2-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="700e2-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="700e2-103">\<system.identityModel></span></span>  
<span data-ttu-id="700e2-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="700e2-104">\<identityConfiguration></span></span>  
<span data-ttu-id="700e2-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="700e2-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="700e2-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="700e2-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="700e2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="700e2-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="700e2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="700e2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="700e2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="700e2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="700e2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="700e2-110">Attributes</span></span>  
  
|<span data-ttu-id="700e2-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="700e2-111">Attribute</span></span>|<span data-ttu-id="700e2-112">Opis</span><span class="sxs-lookup"><span data-stu-id="700e2-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="700e2-113">— typ</span><span class="sxs-lookup"><span data-stu-id="700e2-113">type</span></span>|<span data-ttu-id="700e2-114">Typ zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="700e2-114">The claim type.</span></span> <span data-ttu-id="700e2-115">Zwykle jest to identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="700e2-115">Typically a URI.</span></span> <span data-ttu-id="700e2-116">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="700e2-116">Required.</span></span>|  
|<span data-ttu-id="700e2-117">optional</span><span class="sxs-lookup"><span data-stu-id="700e2-117">optional</span></span>|<span data-ttu-id="700e2-118">Wartość logiczna określająca, czy typ zgłoszenia jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="700e2-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="700e2-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="700e2-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="700e2-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="700e2-120">Child Elements</span></span>  
 <span data-ttu-id="700e2-121">Brak</span><span class="sxs-lookup"><span data-stu-id="700e2-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="700e2-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="700e2-122">Parent Elements</span></span>  
  
|<span data-ttu-id="700e2-123">Element</span><span class="sxs-lookup"><span data-stu-id="700e2-123">Element</span></span>|<span data-ttu-id="700e2-124">Opis</span><span class="sxs-lookup"><span data-stu-id="700e2-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="700e2-125">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="700e2-125">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="700e2-126">Określa zestaw wymaganych oświadczeń dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="700e2-126">Specifies the set of required claims for incoming security tokens.</span></span>|
