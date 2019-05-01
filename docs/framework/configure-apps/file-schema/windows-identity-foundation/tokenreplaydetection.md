---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 4deeb1d84f2621adb7ff1b649a505138b6856ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790497"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="cc1d4-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="cc1d4-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="cc1d4-102">Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="cc1d4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cc1d4-103">\<system.identityModel></span></span>  
<span data-ttu-id="cc1d4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cc1d4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="cc1d4-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="cc1d4-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1d4-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc1d4-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="cc1d4-107">Typ</span><span class="sxs-lookup"><span data-stu-id="cc1d4-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc1d4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cc1d4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cc1d4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc1d4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cc1d4-110">Attributes</span></span>  
  
|<span data-ttu-id="cc1d4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cc1d4-111">Attribute</span></span>|<span data-ttu-id="cc1d4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="cc1d4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cc1d4-113">Włączone</span><span class="sxs-lookup"><span data-stu-id="cc1d4-113">enabled</span></span>|<span data-ttu-id="cc1d4-114">Wartość, która określa, czy jest włączone wykrywanie powtórzeń tokenów; "true", aby umożliwić token wykrywania powtarzania.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="cc1d4-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="cc1d4-115">expirationPeriod</span></span>|<span data-ttu-id="cc1d4-116">Element <xref:System.TimeSpan> , który określa maksymalną ilość czasu, zanim element zostanie uznane za wygasłe i usuwane z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="cc1d4-117">Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc1d4-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cc1d4-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cc1d4-118">Child Elements</span></span>  
 <span data-ttu-id="cc1d4-119">Brak</span><span class="sxs-lookup"><span data-stu-id="cc1d4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cc1d4-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cc1d4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cc1d4-121">Element</span><span class="sxs-lookup"><span data-stu-id="cc1d4-121">Element</span></span>|<span data-ttu-id="cc1d4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="cc1d4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc1d4-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cc1d4-123">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="cc1d4-124">Określa ustawienia tożsamości na poziomie usługi.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="cc1d4-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="cc1d4-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="cc1d4-126">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc1d4-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc1d4-127">Remarks</span></span>  
 <span data-ttu-id="cc1d4-128">A `<tokenReplayDetection>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="cc1d4-129">Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="cc1d4-130">Typ pamięci podręcznej powtórzeń tokenów jest określany przez [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="cc1d4-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
