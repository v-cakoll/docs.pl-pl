---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="96c58-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="96c58-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="96c58-103">Określa zestaw żądanych oświadczeń przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="96c58-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="96c58-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="96c58-104">\<system.identityModel></span></span>  
<span data-ttu-id="96c58-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="96c58-105">\<identityConfiguration></span></span>  
<span data-ttu-id="96c58-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="96c58-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96c58-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="96c58-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96c58-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="96c58-108">Attributes and Elements</span></span>  
 <span data-ttu-id="96c58-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="96c58-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96c58-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="96c58-110">Attributes</span></span>  
 <span data-ttu-id="96c58-111">Brak</span><span class="sxs-lookup"><span data-stu-id="96c58-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96c58-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="96c58-112">Child Elements</span></span>  
  
|<span data-ttu-id="96c58-113">Element</span><span class="sxs-lookup"><span data-stu-id="96c58-113">Element</span></span>|<span data-ttu-id="96c58-114">Opis</span><span class="sxs-lookup"><span data-stu-id="96c58-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96c58-115">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="96c58-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="96c58-116">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="96c58-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96c58-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="96c58-117">Parent Elements</span></span>  
  
|<span data-ttu-id="96c58-118">Element</span><span class="sxs-lookup"><span data-stu-id="96c58-118">Element</span></span>|<span data-ttu-id="96c58-119">Opis</span><span class="sxs-lookup"><span data-stu-id="96c58-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96c58-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="96c58-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="96c58-121">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="96c58-121">Specifies service-level identity settings.</span></span>|
