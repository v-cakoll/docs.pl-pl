---
title: '&lt;audienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3ce884c19d205df4727dcce96ffdf34144ff1dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="b02b4-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="b02b4-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="b02b4-103">Określa zestaw identyfikatorów URI, które są dopuszczalne identyfikatory uzależnionej (RP).</span><span class="sxs-lookup"><span data-stu-id="b02b4-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="b02b4-104">Tokeny nie będą akceptowane, chyba że ograniczone do jednej z dozwolonych odbiorców identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="b02b4-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="b02b4-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b02b4-105">\<system.identityModel></span></span>  
<span data-ttu-id="b02b4-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b02b4-106">\<identityConfiguration></span></span>  
<span data-ttu-id="b02b4-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b02b4-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b02b4-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b02b4-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="b02b4-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="b02b4-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b02b4-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b02b4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b02b4-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b02b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b02b4-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b02b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b02b4-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b02b4-113">Attributes</span></span>  
  
|<span data-ttu-id="b02b4-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b02b4-114">Attribute</span></span>|<span data-ttu-id="b02b4-115">Opis</span><span class="sxs-lookup"><span data-stu-id="b02b4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b02b4-116">tryb</span><span class="sxs-lookup"><span data-stu-id="b02b4-116">mode</span></span>|<span data-ttu-id="b02b4-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość, która określa, czy ograniczenie odbiorców powinien być zastosowany przychodzącym tokenie.</span><span class="sxs-lookup"><span data-stu-id="b02b4-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="b02b4-118">Możliwe wartości to "Always", "Nigdy" i "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="b02b4-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="b02b4-119">Wartość domyślna to "Always".</span><span class="sxs-lookup"><span data-stu-id="b02b4-119">The default is "Always".</span></span> <span data-ttu-id="b02b4-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b02b4-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b02b4-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b02b4-121">Child Elements</span></span>  
  
|<span data-ttu-id="b02b4-122">Element</span><span class="sxs-lookup"><span data-stu-id="b02b4-122">Element</span></span>|<span data-ttu-id="b02b4-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b02b4-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="b02b4-124">Dodaje określony przez identyfikator URI `value` atrybutu do kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="b02b4-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="b02b4-125">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="b02b4-125">The `value` attribute is required.</span></span> <span data-ttu-id="b02b4-126">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b02b4-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="b02b4-127">Czyści kolekcję audienceUris.</span><span class="sxs-lookup"><span data-stu-id="b02b4-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="b02b4-128">Wszystkie identyfikatory zostaną usunięte z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b02b4-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="b02b4-129">Usuwa określony przez identyfikator URI `value` atrybutu z kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="b02b4-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="b02b4-130">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="b02b4-130">The `value` attribute is required.</span></span> <span data-ttu-id="b02b4-131">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="b02b4-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b02b4-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b02b4-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b02b4-133">Element</span><span class="sxs-lookup"><span data-stu-id="b02b4-133">Element</span></span>|<span data-ttu-id="b02b4-134">Opis</span><span class="sxs-lookup"><span data-stu-id="b02b4-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b02b4-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b02b4-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="b02b4-136">Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b02b4-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b02b4-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b02b4-137">Remarks</span></span>  
 <span data-ttu-id="b02b4-138">Domyślnie kolekcji jest pusty; Użyj `<add>`, `<clear>`, i `<remove>` elementy, aby modyfikować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b02b4-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="b02b4-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>i <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> obiekty używają wartości do kolekcji identyfikatora URI odbiorców do skonfigurowania wszystkich dozwolone odbiorców ograniczenia identyfikatora URI w <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="b02b4-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="b02b4-140">`<audienceUris>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="b02b4-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="b02b4-141">URI poszczególnych dodać do kolekcji jest reprezentowane przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="b02b4-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b02b4-142">Korzystanie z `<audienceUris>` element jako element podrzędny elementu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element jest przestarzała, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="b02b4-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b02b4-143">Ustawienia na `<securityTokenHandlerConfiguration>` element przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b02b4-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b02b4-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="b02b4-144">Example</span></span>  
 <span data-ttu-id="b02b4-145">Następujący kod XML przedstawiono sposób konfigurowania odbiorców dopuszczalne identyfikatorów URI dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b02b4-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="b02b4-146">Ten przykład konfiguruje pojedynczy identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="b02b4-146">This example configures a single URI.</span></span> <span data-ttu-id="b02b4-147">Tokeny tego identyfikatora URI w zakresie będą akceptowane, wszystkie pozostałe zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="b02b4-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
