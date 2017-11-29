---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f95d200f74621a40d2987acf68bc554df8d17ab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="59ee9-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="59ee9-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="59ee9-103">Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="59ee9-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="59ee9-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="59ee9-104">\<system.identityModel></span></span>  
<span data-ttu-id="59ee9-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="59ee9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="59ee9-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="59ee9-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59ee9-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="59ee9-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="59ee9-108">Typ</span><span class="sxs-lookup"><span data-stu-id="59ee9-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ee9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="59ee9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="59ee9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="59ee9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ee9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="59ee9-111">Attributes</span></span>  
  
|<span data-ttu-id="59ee9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="59ee9-112">Attribute</span></span>|<span data-ttu-id="59ee9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="59ee9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59ee9-114">włączone</span><span class="sxs-lookup"><span data-stu-id="59ee9-114">enabled</span></span>|<span data-ttu-id="59ee9-115">Wartość określająca, czy jest włączone wykrywanie powtórzeń tokenów; "true", aby włączyć token wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="59ee9-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="59ee9-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="59ee9-116">expirationPeriod</span></span>|<span data-ttu-id="59ee9-117">A <xref:System.TimeSpan> , który określa maksymalną ilość czasu, zanim element zostanie uznane za wygasłe i usuwane z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="59ee9-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="59ee9-118">Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartości Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="59ee9-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59ee9-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="59ee9-119">Child Elements</span></span>  
 <span data-ttu-id="59ee9-120">Brak</span><span class="sxs-lookup"><span data-stu-id="59ee9-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59ee9-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="59ee9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="59ee9-122">Element</span><span class="sxs-lookup"><span data-stu-id="59ee9-122">Element</span></span>|<span data-ttu-id="59ee9-123">Opis</span><span class="sxs-lookup"><span data-stu-id="59ee9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59ee9-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="59ee9-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="59ee9-125">Określa ustawienia tożsamości poziomu usług.</span><span class="sxs-lookup"><span data-stu-id="59ee9-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="59ee9-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="59ee9-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="59ee9-127">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="59ee9-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59ee9-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59ee9-128">Remarks</span></span>  
 <span data-ttu-id="59ee9-129">A `<tokenReplayDetection>` elementu można określić na poziomie usługi pod `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w obszarze `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="59ee9-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="59ee9-130">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="59ee9-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="59ee9-131">Typ pamięci podręcznej powtórzeń tokenów jest określany przez [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="59ee9-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
