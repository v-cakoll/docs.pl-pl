---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: dfa6c0d84582d55595f00f149adfdcaa9d554d6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271957"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="26110-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="26110-101">\<tokenReplayCache></span></span>
<span data-ttu-id="26110-102">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="26110-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="26110-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="26110-103">\<system.identityModel></span></span>  
<span data-ttu-id="26110-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="26110-104">\<identityConfiguration></span></span>  
<span data-ttu-id="26110-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="26110-105">\<caches></span></span>  
<span data-ttu-id="26110-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="26110-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26110-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="26110-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="26110-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="26110-108">Attributes and Elements</span></span>  
 <span data-ttu-id="26110-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="26110-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="26110-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="26110-110">Attributes</span></span>  
  
|<span data-ttu-id="26110-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="26110-111">Attribute</span></span>|<span data-ttu-id="26110-112">Opis</span><span class="sxs-lookup"><span data-stu-id="26110-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26110-113">— typ</span><span class="sxs-lookup"><span data-stu-id="26110-113">type</span></span>|<span data-ttu-id="26110-114">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="26110-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="26110-115">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="26110-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="26110-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="26110-116">Child Elements</span></span>  
 <span data-ttu-id="26110-117">Brak</span><span class="sxs-lookup"><span data-stu-id="26110-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="26110-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="26110-118">Parent Elements</span></span>  
  
|<span data-ttu-id="26110-119">Element</span><span class="sxs-lookup"><span data-stu-id="26110-119">Element</span></span>|<span data-ttu-id="26110-120">Opis</span><span class="sxs-lookup"><span data-stu-id="26110-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="26110-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="26110-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="26110-122">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="26110-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26110-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26110-123">Remarks</span></span>  
 <span data-ttu-id="26110-124">Pamięci podręcznej powtórzeń tokenów jest używana do wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="26110-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="26110-125">Wykrywanie powtórzeń tokenów jest włączane przez [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, który określa również czas wygaśnięcia maksymalna tokenów.</span><span class="sxs-lookup"><span data-stu-id="26110-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26110-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="26110-126">Example</span></span>  
 <span data-ttu-id="26110-127">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="26110-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26110-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26110-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="26110-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="26110-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
