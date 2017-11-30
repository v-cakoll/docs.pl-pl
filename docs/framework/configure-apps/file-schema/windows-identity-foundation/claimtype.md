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
ms.openlocfilehash: c4ee8833578b082f25c427b13d77072d1954197f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="97d5a-102">&lt;Typ oświadczenia&gt;</span><span class="sxs-lookup"><span data-stu-id="97d5a-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="97d5a-103">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="97d5a-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="97d5a-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="97d5a-104">\<system.identityModel></span></span>  
<span data-ttu-id="97d5a-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="97d5a-105">\<identityConfiguration></span></span>  
<span data-ttu-id="97d5a-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="97d5a-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="97d5a-107">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="97d5a-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d5a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="97d5a-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="97d5a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="97d5a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="97d5a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="97d5a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="97d5a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="97d5a-111">Attributes</span></span>  
  
|<span data-ttu-id="97d5a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="97d5a-112">Attribute</span></span>|<span data-ttu-id="97d5a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="97d5a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="97d5a-114">— typ</span><span class="sxs-lookup"><span data-stu-id="97d5a-114">type</span></span>|<span data-ttu-id="97d5a-115">Typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="97d5a-115">The claim type.</span></span> <span data-ttu-id="97d5a-116">Zazwyczaj identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="97d5a-116">Typically a URI.</span></span> <span data-ttu-id="97d5a-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="97d5a-117">Required.</span></span>|  
|<span data-ttu-id="97d5a-118">optional</span><span class="sxs-lookup"><span data-stu-id="97d5a-118">optional</span></span>|<span data-ttu-id="97d5a-119">Wartość logiczna określająca, czy typ oświadczenia jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="97d5a-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="97d5a-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="97d5a-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="97d5a-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="97d5a-121">Child Elements</span></span>  
 <span data-ttu-id="97d5a-122">Brak</span><span class="sxs-lookup"><span data-stu-id="97d5a-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="97d5a-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="97d5a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="97d5a-124">Element</span><span class="sxs-lookup"><span data-stu-id="97d5a-124">Element</span></span>|<span data-ttu-id="97d5a-125">Opis</span><span class="sxs-lookup"><span data-stu-id="97d5a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="97d5a-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="97d5a-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="97d5a-127">Określa zestaw żądanych oświadczeń przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="97d5a-127">Specifies the set of required claims for incoming security tokens.</span></span>|
