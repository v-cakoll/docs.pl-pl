---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1567c669b5e682a7a771d7bedc95a8effa474e36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790510"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="1e6fa-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="1e6fa-101">\<tokenReplayCache></span></span>
<span data-ttu-id="1e6fa-102">Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="1e6fa-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1e6fa-103">\<system.identityModel></span></span>  
<span data-ttu-id="1e6fa-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1e6fa-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1e6fa-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="1e6fa-105">\<caches></span></span>  
<span data-ttu-id="1e6fa-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="1e6fa-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e6fa-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e6fa-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e6fa-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1e6fa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e6fa-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e6fa-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1e6fa-110">Attributes</span></span>  
  
|<span data-ttu-id="1e6fa-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1e6fa-111">Attribute</span></span>|<span data-ttu-id="1e6fa-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1e6fa-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e6fa-113">— typ</span><span class="sxs-lookup"><span data-stu-id="1e6fa-113">type</span></span>|<span data-ttu-id="1e6fa-114">Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.TokenReplayCache> klasy.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="1e6fa-115">Aby uzyskać więcej informacji o sposobie określania niestandardowej `type`, zobacz [odwołań do niestandardowego typu].</span><span class="sxs-lookup"><span data-stu-id="1e6fa-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="1e6fa-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1e6fa-116">Child Elements</span></span>  
 <span data-ttu-id="1e6fa-117">Brak</span><span class="sxs-lookup"><span data-stu-id="1e6fa-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e6fa-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1e6fa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1e6fa-119">Element</span><span class="sxs-lookup"><span data-stu-id="1e6fa-119">Element</span></span>|<span data-ttu-id="1e6fa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1e6fa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e6fa-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="1e6fa-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="1e6fa-122">Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e6fa-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e6fa-123">Remarks</span></span>  
 <span data-ttu-id="1e6fa-124">Pamięci podręcznej powtórzeń tokenów jest używana do wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="1e6fa-125">Wykrywanie powtórzeń tokenów jest włączane przez [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, który określa również czas wygaśnięcia maksymalna tokenów.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e6fa-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="1e6fa-126">Example</span></span>  
 <span data-ttu-id="1e6fa-127">Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej wykrywania powtórzonym tokenów.</span><span class="sxs-lookup"><span data-stu-id="1e6fa-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e6fa-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e6fa-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="1e6fa-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="1e6fa-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
