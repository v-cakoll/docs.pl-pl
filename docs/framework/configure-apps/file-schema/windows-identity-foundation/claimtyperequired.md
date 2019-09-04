---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252054"
---
# <a name="claimtyperequired"></a><span data-ttu-id="06d80-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="06d80-101">\<claimTypeRequired></span></span>
<span data-ttu-id="06d80-102">Określa zestaw wymaganych oświadczeń dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="06d80-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
<span data-ttu-id="06d80-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06d80-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06d80-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="06d80-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="06d80-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="06d80-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="06d80-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimTypeRequired >**</span><span class="sxs-lookup"><span data-stu-id="06d80-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d80-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="06d80-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06d80-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="06d80-108">Attributes and Elements</span></span>  
 <span data-ttu-id="06d80-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="06d80-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06d80-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="06d80-110">Attributes</span></span>  
 <span data-ttu-id="06d80-111">Brak</span><span class="sxs-lookup"><span data-stu-id="06d80-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06d80-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="06d80-112">Child Elements</span></span>  
  
|<span data-ttu-id="06d80-113">Element</span><span class="sxs-lookup"><span data-stu-id="06d80-113">Element</span></span>|<span data-ttu-id="06d80-114">Opis</span><span class="sxs-lookup"><span data-stu-id="06d80-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06d80-115">\<claimType></span><span class="sxs-lookup"><span data-stu-id="06d80-115">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="06d80-116">Określa jedno opcjonalne lub wymagane żądanie dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="06d80-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06d80-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="06d80-117">Parent Elements</span></span>  
  
|<span data-ttu-id="06d80-118">Element</span><span class="sxs-lookup"><span data-stu-id="06d80-118">Element</span></span>|<span data-ttu-id="06d80-119">Opis</span><span class="sxs-lookup"><span data-stu-id="06d80-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06d80-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="06d80-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="06d80-121">Określa ustawienia tożsamości na poziomie usług.</span><span class="sxs-lookup"><span data-stu-id="06d80-121">Specifies service-level identity settings.</span></span>|
