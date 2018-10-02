---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: bd2272cb83dc0183d5008cfa178e11783f51ca2d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48031987"
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="44465-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="44465-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="44465-103">Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="44465-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="44465-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="44465-104">\<system.identityModel></span></span>  
<span data-ttu-id="44465-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="44465-105">\<identityConfiguration></span></span>  
<span data-ttu-id="44465-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="44465-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44465-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="44465-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="44465-108">Typ</span><span class="sxs-lookup"><span data-stu-id="44465-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44465-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44465-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44465-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44465-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44465-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44465-111">Attributes</span></span>  
  
|<span data-ttu-id="44465-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44465-112">Attribute</span></span>|<span data-ttu-id="44465-113">Opis</span><span class="sxs-lookup"><span data-stu-id="44465-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44465-114">Włączone</span><span class="sxs-lookup"><span data-stu-id="44465-114">enabled</span></span>|<span data-ttu-id="44465-115">Wartość, która określa, czy jest włączone wykrywanie powtórzeń tokenów; "true", aby umożliwić token wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="44465-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="44465-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="44465-116">expirationPeriod</span></span>|<span data-ttu-id="44465-117">Element <xref:System.TimeSpan> , który określa maksymalną ilość czasu, zanim element zostanie uznane za wygasłe i usuwane z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="44465-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="44465-118">Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="44465-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44465-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44465-119">Child Elements</span></span>  
 <span data-ttu-id="44465-120">Brak</span><span class="sxs-lookup"><span data-stu-id="44465-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44465-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44465-121">Parent Elements</span></span>  
  
|<span data-ttu-id="44465-122">Element</span><span class="sxs-lookup"><span data-stu-id="44465-122">Element</span></span>|<span data-ttu-id="44465-123">Opis</span><span class="sxs-lookup"><span data-stu-id="44465-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44465-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="44465-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="44465-125">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="44465-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="44465-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="44465-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="44465-127">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="44465-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44465-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44465-128">Remarks</span></span>  
 <span data-ttu-id="44465-129">A `<tokenReplayDetection>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="44465-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="44465-130">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="44465-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="44465-131">Typ pamięci podręcznej powtórzeń tokenów jest określany przez [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="44465-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
