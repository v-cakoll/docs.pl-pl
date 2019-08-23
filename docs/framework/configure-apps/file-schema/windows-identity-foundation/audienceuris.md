---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941961"
---
# <a name="audienceuris"></a><span data-ttu-id="95757-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="95757-101">\<audienceUris></span></span>
<span data-ttu-id="95757-102">Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami jednostki uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="95757-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="95757-103">Tokeny nie zostaną zaakceptowane, chyba że zostaną objęte zakresem jednego z dozwolonych identyfikatorów URI odbiorców.</span><span class="sxs-lookup"><span data-stu-id="95757-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="95757-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="95757-104">\<system.identityModel></span></span>  
<span data-ttu-id="95757-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="95757-105">\<identityConfiguration></span></span>  
<span data-ttu-id="95757-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="95757-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="95757-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="95757-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="95757-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="95757-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95757-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="95757-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95757-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95757-110">Attributes and Elements</span></span>  
 <span data-ttu-id="95757-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95757-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95757-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95757-112">Attributes</span></span>  
  
|<span data-ttu-id="95757-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95757-113">Attribute</span></span>|<span data-ttu-id="95757-114">Opis</span><span class="sxs-lookup"><span data-stu-id="95757-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95757-115">tryb</span><span class="sxs-lookup"><span data-stu-id="95757-115">mode</span></span>|<span data-ttu-id="95757-116"><xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość określająca, czy ograniczenie odbiorców ma być stosowane do tokenu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="95757-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="95757-117">Możliwe wartości to "always", "Never" i "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="95757-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="95757-118">Wartość domyślna to "zawsze".</span><span class="sxs-lookup"><span data-stu-id="95757-118">The default is "Always".</span></span> <span data-ttu-id="95757-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="95757-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95757-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95757-120">Child Elements</span></span>  
  
|<span data-ttu-id="95757-121">Element</span><span class="sxs-lookup"><span data-stu-id="95757-121">Element</span></span>|<span data-ttu-id="95757-122">Opis</span><span class="sxs-lookup"><span data-stu-id="95757-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="95757-123">Dodaje identyfikator URI określony przez `value` atrybut do kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="95757-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="95757-124">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="95757-124">The `value` attribute is required.</span></span> <span data-ttu-id="95757-125">W identyfikatorze URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="95757-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="95757-126">Czyści kolekcję audienceUris.</span><span class="sxs-lookup"><span data-stu-id="95757-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="95757-127">Wszystkie identyfikatory są usuwane z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="95757-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="95757-128">Usuwa identyfikator URI określony przez `value` atrybut z kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="95757-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="95757-129">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="95757-129">The `value` attribute is required.</span></span> <span data-ttu-id="95757-130">W identyfikatorze URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="95757-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95757-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95757-131">Parent Elements</span></span>  
  
|<span data-ttu-id="95757-132">Element</span><span class="sxs-lookup"><span data-stu-id="95757-132">Element</span></span>|<span data-ttu-id="95757-133">Opis</span><span class="sxs-lookup"><span data-stu-id="95757-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95757-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="95757-134">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="95757-135">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="95757-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95757-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95757-136">Remarks</span></span>  
 <span data-ttu-id="95757-137">Domyślnie kolekcja jest pusta; Użyj `<add>`elementów `<clear>`, i`<remove>` , aby zmodyfikować kolekcję.</span><span class="sxs-lookup"><span data-stu-id="95757-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="95757-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>obiekty <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> i używają wartości w kolekcji identyfikatorów URI odbiorców w celu skonfigurowania dozwolonych ograniczeń identyfikatorów URI <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> odbiorców w obiektach.</span><span class="sxs-lookup"><span data-stu-id="95757-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="95757-139">Element jest reprezentowany <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> przez klasę. `<audienceUris>`</span><span class="sxs-lookup"><span data-stu-id="95757-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="95757-140">Pojedynczy identyfikator URI dodany do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="95757-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95757-141">Użycie `<audienceUris>` elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="95757-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="95757-142">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="95757-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95757-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="95757-143">Example</span></span>  
 <span data-ttu-id="95757-144">Poniższy kod XML przedstawia sposób konfigurowania akceptowalnych identyfikatorów URI odbiorców dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95757-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="95757-145">Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="95757-145">This example configures a single URI.</span></span> <span data-ttu-id="95757-146">Tokeny należące do zakresu dla tego identyfikatora URI zostaną zaakceptowane. wszystkie pozostałe zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="95757-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
