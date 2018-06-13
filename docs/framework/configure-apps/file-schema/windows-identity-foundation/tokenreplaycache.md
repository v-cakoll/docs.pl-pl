---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 79022319944c4042c6f62a7521784b826b90d4ce
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755126"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="ab47f-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="ab47f-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="ab47f-103">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ab47f-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="ab47f-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ab47f-104">\<system.identityModel></span></span>  
<span data-ttu-id="ab47f-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ab47f-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ab47f-106">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="ab47f-106">\<caches></span></span>  
<span data-ttu-id="ab47f-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="ab47f-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab47f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab47f-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab47f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ab47f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab47f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ab47f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab47f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ab47f-111">Attributes</span></span>  
  
|<span data-ttu-id="ab47f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ab47f-112">Attribute</span></span>|<span data-ttu-id="ab47f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ab47f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab47f-114">— typ</span><span class="sxs-lookup"><span data-stu-id="ab47f-114">type</span></span>|<span data-ttu-id="ab47f-115">Typ, który pochodzi z <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="ab47f-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="ab47f-116">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołania do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="ab47f-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ab47f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ab47f-117">Child Elements</span></span>  
 <span data-ttu-id="ab47f-118">Brak</span><span class="sxs-lookup"><span data-stu-id="ab47f-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab47f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab47f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ab47f-120">Element</span><span class="sxs-lookup"><span data-stu-id="ab47f-120">Element</span></span>|<span data-ttu-id="ab47f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="ab47f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab47f-122">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="ab47f-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="ab47f-123">Rejestruje pamięci podręcznych, używany przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ab47f-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab47f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab47f-124">Remarks</span></span>  
 <span data-ttu-id="ab47f-125">Pamięci podręcznej powtórzeń tokenów jest używana do wykrywania tokeny powtórzony.</span><span class="sxs-lookup"><span data-stu-id="ab47f-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="ab47f-126">Wykrywanie powtórzeń tokenów jest włączana przez [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, który również określa czas maksymalny wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="ab47f-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab47f-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab47f-127">Example</span></span>  
 <span data-ttu-id="ab47f-128">Następujący kod XML zawiera konfiguracji niestandardowej pamięci podręcznej wykrywania tokeny powtórzony.</span><span class="sxs-lookup"><span data-stu-id="ab47f-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab47f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab47f-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="ab47f-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="ab47f-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
