---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: df4494de6b76943849db2bedef8f43ad894b6bd1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47399414"
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="31fc1-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="31fc1-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="31fc1-103">Określa zestaw wymagane oświadczenia przychodzące tokeny zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="31fc1-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="31fc1-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="31fc1-104">\<system.identityModel></span></span>  
<span data-ttu-id="31fc1-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="31fc1-105">\<identityConfiguration></span></span>  
<span data-ttu-id="31fc1-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="31fc1-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fc1-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="31fc1-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31fc1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="31fc1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="31fc1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="31fc1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31fc1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="31fc1-110">Attributes</span></span>  
 <span data-ttu-id="31fc1-111">Brak</span><span class="sxs-lookup"><span data-stu-id="31fc1-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="31fc1-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="31fc1-112">Child Elements</span></span>  
  
|<span data-ttu-id="31fc1-113">Element</span><span class="sxs-lookup"><span data-stu-id="31fc1-113">Element</span></span>|<span data-ttu-id="31fc1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="31fc1-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31fc1-115">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="31fc1-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="31fc1-116">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="31fc1-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31fc1-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="31fc1-117">Parent Elements</span></span>  
  
|<span data-ttu-id="31fc1-118">Element</span><span class="sxs-lookup"><span data-stu-id="31fc1-118">Element</span></span>|<span data-ttu-id="31fc1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="31fc1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31fc1-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="31fc1-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="31fc1-121">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="31fc1-121">Specifies service-level identity settings.</span></span>|
