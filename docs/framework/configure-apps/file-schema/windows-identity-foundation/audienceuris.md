---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7415cb3f1792d2de566161ae6c348ef591b4a0c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755997"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="61de0-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="61de0-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="61de0-103">Określa zestaw identyfikatorów URI, które są dopuszczalne identyfikatory uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="61de0-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="61de0-104">Tokeny nie będą akceptowane, chyba że ograniczone do jednej z dozwolonych odbiorców identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="61de0-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="61de0-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="61de0-105">\<system.identityModel></span></span>  
<span data-ttu-id="61de0-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="61de0-106">\<identityConfiguration></span></span>  
<span data-ttu-id="61de0-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="61de0-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="61de0-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="61de0-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="61de0-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="61de0-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61de0-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="61de0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61de0-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61de0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="61de0-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61de0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61de0-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61de0-113">Attributes</span></span>  
  
|<span data-ttu-id="61de0-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61de0-114">Attribute</span></span>|<span data-ttu-id="61de0-115">Opis</span><span class="sxs-lookup"><span data-stu-id="61de0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="61de0-116">tryb</span><span class="sxs-lookup"><span data-stu-id="61de0-116">mode</span></span>|<span data-ttu-id="61de0-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość, która określa, czy ograniczenie odbiorców powinien być zastosowany przychodzącym tokenie.</span><span class="sxs-lookup"><span data-stu-id="61de0-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="61de0-118">Możliwe wartości to "Always", "Nigdy" i "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="61de0-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="61de0-119">Wartość domyślna to "Always".</span><span class="sxs-lookup"><span data-stu-id="61de0-119">The default is "Always".</span></span> <span data-ttu-id="61de0-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="61de0-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61de0-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61de0-121">Child Elements</span></span>  
  
|<span data-ttu-id="61de0-122">Element</span><span class="sxs-lookup"><span data-stu-id="61de0-122">Element</span></span>|<span data-ttu-id="61de0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="61de0-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="61de0-124">Dodaje określony przez identyfikator URI `value` atrybutu do kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="61de0-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="61de0-125">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="61de0-125">The `value` attribute is required.</span></span> <span data-ttu-id="61de0-126">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="61de0-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="61de0-127">Czyści kolekcję audienceUris.</span><span class="sxs-lookup"><span data-stu-id="61de0-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="61de0-128">Wszystkie identyfikatory zostaną usunięte z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61de0-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="61de0-129">Usuwa określony przez identyfikator URI `value` atrybutu z kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="61de0-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="61de0-130">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="61de0-130">The `value` attribute is required.</span></span> <span data-ttu-id="61de0-131">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="61de0-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61de0-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61de0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="61de0-133">Element</span><span class="sxs-lookup"><span data-stu-id="61de0-133">Element</span></span>|<span data-ttu-id="61de0-134">Opis</span><span class="sxs-lookup"><span data-stu-id="61de0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="61de0-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="61de0-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="61de0-136">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="61de0-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61de0-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61de0-137">Remarks</span></span>  
 <span data-ttu-id="61de0-138">Domyślnie kolekcji jest pusty; Użyj `<add>`, `<clear>`, i `<remove>` elementy, aby modyfikować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="61de0-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="61de0-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> i <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> obiekty używają wartości do kolekcji identyfikatora URI odbiorców do skonfigurowania wszystkich dozwolone odbiorców ograniczenia identyfikatora URI w <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="61de0-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="61de0-140">`<audienceUris>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="61de0-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="61de0-141">URI poszczególnych dodać do kolekcji jest reprezentowane przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="61de0-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61de0-142">Korzystanie z `<audienceUris>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="61de0-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="61de0-143">Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="61de0-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61de0-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="61de0-144">Example</span></span>  
 <span data-ttu-id="61de0-145">Następujący kod XML przedstawiono sposób konfigurowania odbiorców dopuszczalne identyfikatorów URI dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="61de0-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="61de0-146">Ten przykład konfiguruje pojedynczy identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="61de0-146">This example configures a single URI.</span></span> <span data-ttu-id="61de0-147">Tokeny tego identyfikatora URI w zakresie będą akceptowane, wszystkie pozostałe zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="61de0-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
