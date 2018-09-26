---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082451"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="a7bf9-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="a7bf9-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="a7bf9-103">Określa zbiór identyfikatorów URI, które są dopuszczalne identyfikatorów jednostki uzależnionej strony (RP).</span><span class="sxs-lookup"><span data-stu-id="a7bf9-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="a7bf9-104">Tokeny nie będą akceptowane, chyba że są one w zakresie dla jednej z dozwolonych odbiorców identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="a7bf9-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a7bf9-105">\<system.identityModel></span></span>  
<span data-ttu-id="a7bf9-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a7bf9-106">\<identityConfiguration></span></span>  
<span data-ttu-id="a7bf9-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a7bf9-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a7bf9-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a7bf9-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="a7bf9-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="a7bf9-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7bf9-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7bf9-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7bf9-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a7bf9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a7bf9-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7bf9-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a7bf9-113">Attributes</span></span>  
  
|<span data-ttu-id="a7bf9-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7bf9-114">Attribute</span></span>|<span data-ttu-id="a7bf9-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a7bf9-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7bf9-116">tryb</span><span class="sxs-lookup"><span data-stu-id="a7bf9-116">mode</span></span>|<span data-ttu-id="a7bf9-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość, która określa, czy ograniczenie odbiorców powinny być stosowane do przychodzący token.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="a7bf9-118">Możliwe wartości to "Zawsze", "Nie" i "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="a7bf9-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="a7bf9-119">Wartość domyślna to "Always".</span><span class="sxs-lookup"><span data-stu-id="a7bf9-119">The default is "Always".</span></span> <span data-ttu-id="a7bf9-120">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7bf9-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a7bf9-121">Child Elements</span></span>  
  
|<span data-ttu-id="a7bf9-122">Element</span><span class="sxs-lookup"><span data-stu-id="a7bf9-122">Element</span></span>|<span data-ttu-id="a7bf9-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a7bf9-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="a7bf9-124">Dodaje określony przez identyfikator URI `value` atrybutu do kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="a7bf9-125">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-125">The `value` attribute is required.</span></span> <span data-ttu-id="a7bf9-126">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="a7bf9-127">Czyści kolekcję audienceUris.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="a7bf9-128">Wszystkie identyfikatory są usuwane z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="a7bf9-129">Usuwa określony przez identyfikator URI `value` atrybutu z kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="a7bf9-130">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-130">The `value` attribute is required.</span></span> <span data-ttu-id="a7bf9-131">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7bf9-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a7bf9-132">Parent Elements</span></span>  
  
|<span data-ttu-id="a7bf9-133">Element</span><span class="sxs-lookup"><span data-stu-id="a7bf9-133">Element</span></span>|<span data-ttu-id="a7bf9-134">Opis</span><span class="sxs-lookup"><span data-stu-id="a7bf9-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7bf9-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a7bf9-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="a7bf9-136">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7bf9-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7bf9-137">Remarks</span></span>  
 <span data-ttu-id="a7bf9-138">Domyślnie kolekcja jest pusta, Użyj `<add>`, `<clear>`, i `<remove>` elementy, aby zmodyfikować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="a7bf9-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> i <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> obiekty wartości w kolekcji identyfikatora URI grupy odbiorców do skonfigurowania wszystkich dozwolone odbiorców ograniczeń identyfikatora URI w użycie <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="a7bf9-140">`<audienceUris>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="a7bf9-141">Identyfikator URI poszczególnych dodawane do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7bf9-142">Korzystanie z `<audienceUris>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a7bf9-143">Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7bf9-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7bf9-144">Example</span></span>  
 <span data-ttu-id="a7bf9-145">Następujący kod XML przedstawia sposób konfigurowania odbiorców dopuszczalne identyfikatorów URI dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="a7bf9-146">Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-146">This example configures a single URI.</span></span> <span data-ttu-id="a7bf9-147">Akceptowane są tokeny zakresu dla tego identyfikatora URI, wszystkie pozostałe zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="a7bf9-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
