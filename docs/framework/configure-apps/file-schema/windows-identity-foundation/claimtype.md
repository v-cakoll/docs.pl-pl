---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 6bc185572528d4229ee53f1421eaa5bf27b053e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667226"
---
# <a name="claimtype"></a><span data-ttu-id="7d500-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="7d500-101">\<claimType></span></span>
<span data-ttu-id="7d500-102">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="7d500-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="7d500-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7d500-103">\<system.identityModel></span></span>  
<span data-ttu-id="7d500-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7d500-104">\<identityConfiguration></span></span>  
<span data-ttu-id="7d500-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="7d500-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="7d500-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="7d500-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d500-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d500-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d500-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7d500-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d500-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7d500-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d500-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7d500-110">Attributes</span></span>  
  
|<span data-ttu-id="7d500-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7d500-111">Attribute</span></span>|<span data-ttu-id="7d500-112">Opis</span><span class="sxs-lookup"><span data-stu-id="7d500-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d500-113">— typ</span><span class="sxs-lookup"><span data-stu-id="7d500-113">type</span></span>|<span data-ttu-id="7d500-114">Typ oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="7d500-114">The claim type.</span></span> <span data-ttu-id="7d500-115">Zazwyczaj identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="7d500-115">Typically a URI.</span></span> <span data-ttu-id="7d500-116">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7d500-116">Required.</span></span>|  
|<span data-ttu-id="7d500-117">optional</span><span class="sxs-lookup"><span data-stu-id="7d500-117">optional</span></span>|<span data-ttu-id="7d500-118">Wartość logiczna określająca, czy typ oświadczenia jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="7d500-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="7d500-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7d500-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d500-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7d500-120">Child Elements</span></span>  
 <span data-ttu-id="7d500-121">Brak</span><span class="sxs-lookup"><span data-stu-id="7d500-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d500-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7d500-122">Parent Elements</span></span>  
  
|<span data-ttu-id="7d500-123">Element</span><span class="sxs-lookup"><span data-stu-id="7d500-123">Element</span></span>|<span data-ttu-id="7d500-124">Opis</span><span class="sxs-lookup"><span data-stu-id="7d500-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d500-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="7d500-125">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="7d500-126">Określa zestaw wymagane oświadczenia przychodzące tokeny zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7d500-126">Specifies the set of required claims for incoming security tokens.</span></span>|
