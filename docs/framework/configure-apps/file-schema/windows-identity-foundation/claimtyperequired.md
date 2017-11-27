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
ms.openlocfilehash: 89d42cba78eb9758d8b3491fd1bd3b25ef168f9c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="4fd8c-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="4fd8c-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="4fd8c-103">Określa zestaw żądanych oświadczeń przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="4fd8c-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="4fd8c-104">\<system.identityModel></span></span>  
<span data-ttu-id="4fd8c-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4fd8c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4fd8c-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="4fd8c-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fd8c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4fd8c-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fd8c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4fd8c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4fd8c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fd8c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4fd8c-110">Attributes</span></span>  
 <span data-ttu-id="4fd8c-111">Brak</span><span class="sxs-lookup"><span data-stu-id="4fd8c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4fd8c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4fd8c-112">Child Elements</span></span>  
  
|<span data-ttu-id="4fd8c-113">Element</span><span class="sxs-lookup"><span data-stu-id="4fd8c-113">Element</span></span>|<span data-ttu-id="4fd8c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4fd8c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fd8c-115">\<Element claimType ></span><span class="sxs-lookup"><span data-stu-id="4fd8c-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="4fd8c-116">Określa pojedynczy opcjonalne lub wymagane oświadczenia przychodzące tokeny zabezpieczające.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4fd8c-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4fd8c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4fd8c-118">Element</span><span class="sxs-lookup"><span data-stu-id="4fd8c-118">Element</span></span>|<span data-ttu-id="4fd8c-119">Opis</span><span class="sxs-lookup"><span data-stu-id="4fd8c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fd8c-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4fd8c-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4fd8c-121">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="4fd8c-121">Specifies service-level identity settings.</span></span>|
