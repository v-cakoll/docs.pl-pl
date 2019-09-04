---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252070"
---
# <a name="claimtype"></a><span data-ttu-id="9ed2d-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="9ed2d-101">\<claimType></span></span>
<span data-ttu-id="9ed2d-102">Określa jedno opcjonalne lub wymagane żądanie dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
<span data-ttu-id="9ed2d-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9ed2d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9ed2d-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="9ed2d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="9ed2d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9ed2d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="9ed2d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequired >** ](claimtyperequired.md)</span><span class="sxs-lookup"><span data-stu-id="9ed2d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)</span></span>\  
<span data-ttu-id="9ed2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> oświadczenia**</span><span class="sxs-lookup"><span data-stu-id="9ed2d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed2d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ed2d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ed2d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9ed2d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9ed2d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ed2d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9ed2d-111">Attributes</span></span>  
  
|<span data-ttu-id="9ed2d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9ed2d-112">Attribute</span></span>|<span data-ttu-id="9ed2d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed2d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ed2d-114">— typ</span><span class="sxs-lookup"><span data-stu-id="9ed2d-114">type</span></span>|<span data-ttu-id="9ed2d-115">Typ zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-115">The claim type.</span></span> <span data-ttu-id="9ed2d-116">Zwykle jest to identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-116">Typically a URI.</span></span> <span data-ttu-id="9ed2d-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-117">Required.</span></span>|  
|<span data-ttu-id="9ed2d-118">optional</span><span class="sxs-lookup"><span data-stu-id="9ed2d-118">optional</span></span>|<span data-ttu-id="9ed2d-119">Wartość logiczna określająca, czy typ zgłoszenia jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="9ed2d-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ed2d-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9ed2d-121">Child Elements</span></span>  
 <span data-ttu-id="9ed2d-122">Brak</span><span class="sxs-lookup"><span data-stu-id="9ed2d-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9ed2d-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9ed2d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9ed2d-124">Element</span><span class="sxs-lookup"><span data-stu-id="9ed2d-124">Element</span></span>|<span data-ttu-id="9ed2d-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed2d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ed2d-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="9ed2d-126">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="9ed2d-127">Określa zestaw wymaganych oświadczeń dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="9ed2d-127">Specifies the set of required claims for incoming security tokens.</span></span>|
