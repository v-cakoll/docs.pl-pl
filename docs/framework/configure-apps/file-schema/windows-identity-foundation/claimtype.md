---
title: "&lt;Typ oświadczenia&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ae572ff3a8a2335a4259bdce2af5f6922fb0596f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="8dd60-102">&lt;Typ oświadczenia&gt;</span><span class="sxs-lookup"><span data-stu-id="8dd60-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="8dd60-103">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="8dd60-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="8dd60-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="8dd60-104">\<system.identityModel></span></span>  
<span data-ttu-id="8dd60-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8dd60-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8dd60-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="8dd60-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="8dd60-107">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="8dd60-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dd60-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8dd60-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dd60-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8dd60-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8dd60-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8dd60-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8dd60-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8dd60-111">Attributes</span></span>  
  
|<span data-ttu-id="8dd60-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8dd60-112">Attribute</span></span>|<span data-ttu-id="8dd60-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd60-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8dd60-114">— typ</span><span class="sxs-lookup"><span data-stu-id="8dd60-114">type</span></span>|<span data-ttu-id="8dd60-115">Typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="8dd60-115">The claim type.</span></span> <span data-ttu-id="8dd60-116">Zazwyczaj identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="8dd60-116">Typically a URI.</span></span> <span data-ttu-id="8dd60-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8dd60-117">Required.</span></span>|  
|<span data-ttu-id="8dd60-118">optional</span><span class="sxs-lookup"><span data-stu-id="8dd60-118">optional</span></span>|<span data-ttu-id="8dd60-119">Wartość logiczna określająca, czy typ oświadczenia jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="8dd60-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="8dd60-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8dd60-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8dd60-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8dd60-121">Child Elements</span></span>  
 <span data-ttu-id="8dd60-122">Brak</span><span class="sxs-lookup"><span data-stu-id="8dd60-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8dd60-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8dd60-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8dd60-124">Element</span><span class="sxs-lookup"><span data-stu-id="8dd60-124">Element</span></span>|<span data-ttu-id="8dd60-125">Opis</span><span class="sxs-lookup"><span data-stu-id="8dd60-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8dd60-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="8dd60-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="8dd60-127">Określa zestaw żądanych oświadczeń przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="8dd60-127">Specifies the set of required claims for incoming security tokens.</span></span>|
