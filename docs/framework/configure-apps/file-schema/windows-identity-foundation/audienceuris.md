---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252170"
---
# <a name="audienceuris"></a><span data-ttu-id="91939-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="91939-101">\<audienceUris></span></span>
<span data-ttu-id="91939-102">Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami jednostki uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="91939-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="91939-103">Tokeny nie zostaną zaakceptowane, chyba że zostaną objęte zakresem jednego z dozwolonych identyfikatorów URI odbiorców.</span><span class="sxs-lookup"><span data-stu-id="91939-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
<span data-ttu-id="91939-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91939-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91939-105">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="91939-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="91939-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="91939-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="91939-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="91939-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="91939-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="91939-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="91939-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**</span><span class="sxs-lookup"><span data-stu-id="91939-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91939-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="91939-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91939-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="91939-111">Attributes and Elements</span></span>  
 <span data-ttu-id="91939-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="91939-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91939-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="91939-113">Attributes</span></span>  
  
|<span data-ttu-id="91939-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="91939-114">Attribute</span></span>|<span data-ttu-id="91939-115">Opis</span><span class="sxs-lookup"><span data-stu-id="91939-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91939-116">tryb</span><span class="sxs-lookup"><span data-stu-id="91939-116">mode</span></span>|<span data-ttu-id="91939-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość określająca, czy ograniczenie odbiorców ma być stosowane do tokenu przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="91939-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="91939-118">Możliwe wartości to "always", "Never" i "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="91939-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="91939-119">Wartość domyślna to "zawsze".</span><span class="sxs-lookup"><span data-stu-id="91939-119">The default is "Always".</span></span> <span data-ttu-id="91939-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="91939-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91939-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="91939-121">Child Elements</span></span>  
  
|<span data-ttu-id="91939-122">Element</span><span class="sxs-lookup"><span data-stu-id="91939-122">Element</span></span>|<span data-ttu-id="91939-123">Opis</span><span class="sxs-lookup"><span data-stu-id="91939-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="91939-124">Dodaje identyfikator URI określony przez `value` atrybut do kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="91939-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="91939-125">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="91939-125">The `value` attribute is required.</span></span> <span data-ttu-id="91939-126">W identyfikatorze URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="91939-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="91939-127">Czyści kolekcję audienceUris.</span><span class="sxs-lookup"><span data-stu-id="91939-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="91939-128">Wszystkie identyfikatory są usuwane z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="91939-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="91939-129">Usuwa identyfikator URI określony przez `value` atrybut z kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="91939-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="91939-130">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="91939-130">The `value` attribute is required.</span></span> <span data-ttu-id="91939-131">W identyfikatorze URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="91939-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91939-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="91939-132">Parent Elements</span></span>  
  
|<span data-ttu-id="91939-133">Element</span><span class="sxs-lookup"><span data-stu-id="91939-133">Element</span></span>|<span data-ttu-id="91939-134">Opis</span><span class="sxs-lookup"><span data-stu-id="91939-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91939-135">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="91939-135">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="91939-136">Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="91939-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91939-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91939-137">Remarks</span></span>  
 <span data-ttu-id="91939-138">Domyślnie kolekcja jest pusta; Użyj `<add>`elementów `<clear>`, i`<remove>` , aby zmodyfikować kolekcję.</span><span class="sxs-lookup"><span data-stu-id="91939-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="91939-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>obiekty <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> i używają wartości w kolekcji identyfikatorów URI odbiorców w celu skonfigurowania dozwolonych ograniczeń identyfikatorów URI <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> odbiorców w obiektach.</span><span class="sxs-lookup"><span data-stu-id="91939-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="91939-140">Element jest reprezentowany <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> przez klasę. `<audienceUris>`</span><span class="sxs-lookup"><span data-stu-id="91939-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="91939-141">Pojedynczy identyfikator URI dodany do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="91939-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91939-142">Użycie `<audienceUris>` elementu jako elementu [ \<](identityconfiguration.md) podrzędnego elementu IdentityConfiguration > jest przestarzałe, ale nadal jest obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="91939-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="91939-143">Ustawienia w `<securityTokenHandlerConfiguration>` elemencie Przesłoń te elementy `<identityConfiguration>` w elemencie.</span><span class="sxs-lookup"><span data-stu-id="91939-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91939-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="91939-144">Example</span></span>  
 <span data-ttu-id="91939-145">Poniższy kod XML przedstawia sposób konfigurowania akceptowalnych identyfikatorów URI odbiorców dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91939-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="91939-146">Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="91939-146">This example configures a single URI.</span></span> <span data-ttu-id="91939-147">Tokeny należące do zakresu dla tego identyfikatora URI zostaną zaakceptowane. wszystkie pozostałe zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="91939-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
