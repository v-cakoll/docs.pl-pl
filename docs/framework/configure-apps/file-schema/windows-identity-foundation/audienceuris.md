---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750751"
---
# <a name="audienceuris"></a><span data-ttu-id="edad9-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="edad9-101">\<audienceUris></span></span>
<span data-ttu-id="edad9-102">Określa zbiór identyfikatorów URI, które są dopuszczalne identyfikatorów jednostki uzależnionej strony (RP).</span><span class="sxs-lookup"><span data-stu-id="edad9-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="edad9-103">Tokeny nie będą akceptowane, chyba że są one w zakresie dla jednej z dozwolonych odbiorców identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="edad9-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="edad9-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="edad9-104">\<system.identityModel></span></span>  
<span data-ttu-id="edad9-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="edad9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="edad9-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="edad9-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="edad9-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="edad9-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="edad9-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="edad9-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edad9-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="edad9-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edad9-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="edad9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="edad9-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="edad9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edad9-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="edad9-112">Attributes</span></span>  
  
|<span data-ttu-id="edad9-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="edad9-113">Attribute</span></span>|<span data-ttu-id="edad9-114">Opis</span><span class="sxs-lookup"><span data-stu-id="edad9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edad9-115">tryb</span><span class="sxs-lookup"><span data-stu-id="edad9-115">mode</span></span>|<span data-ttu-id="edad9-116"><xref:System.IdentityModel.Selectors.AudienceUriMode> Wartość, która określa, czy ograniczenie odbiorców powinny być stosowane do przychodzący token.</span><span class="sxs-lookup"><span data-stu-id="edad9-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="edad9-117">Możliwe wartości to "Zawsze", "Nie" i "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="edad9-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="edad9-118">Wartość domyślna to "Always".</span><span class="sxs-lookup"><span data-stu-id="edad9-118">The default is "Always".</span></span> <span data-ttu-id="edad9-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="edad9-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edad9-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="edad9-120">Child Elements</span></span>  
  
|<span data-ttu-id="edad9-121">Element</span><span class="sxs-lookup"><span data-stu-id="edad9-121">Element</span></span>|<span data-ttu-id="edad9-122">Opis</span><span class="sxs-lookup"><span data-stu-id="edad9-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="edad9-123">Dodaje określony przez identyfikator URI `value` atrybutu do kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="edad9-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="edad9-124">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="edad9-124">The `value` attribute is required.</span></span> <span data-ttu-id="edad9-125">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="edad9-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="edad9-126">Czyści kolekcję audienceUris.</span><span class="sxs-lookup"><span data-stu-id="edad9-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="edad9-127">Wszystkie identyfikatory są usuwane z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="edad9-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="edad9-128">Usuwa określony przez identyfikator URI `value` atrybutu z kolekcji audienceUris.</span><span class="sxs-lookup"><span data-stu-id="edad9-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="edad9-129">`value` Atrybut jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="edad9-129">The `value` attribute is required.</span></span> <span data-ttu-id="edad9-130">Identyfikator URI jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="edad9-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="edad9-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="edad9-131">Parent Elements</span></span>  
  
|<span data-ttu-id="edad9-132">Element</span><span class="sxs-lookup"><span data-stu-id="edad9-132">Element</span></span>|<span data-ttu-id="edad9-133">Opis</span><span class="sxs-lookup"><span data-stu-id="edad9-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edad9-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="edad9-134">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="edad9-135">Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="edad9-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edad9-136">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edad9-136">Remarks</span></span>  
 <span data-ttu-id="edad9-137">Domyślnie kolekcja jest pusta, Użyj `<add>`, `<clear>`, i `<remove>` elementy, aby zmodyfikować kolekcji.</span><span class="sxs-lookup"><span data-stu-id="edad9-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="edad9-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> i <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> obiekty wartości w kolekcji identyfikatora URI grupy odbiorców do skonfigurowania wszystkich dozwolone odbiorców ograniczeń identyfikatora URI w użycie <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="edad9-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="edad9-139">`<audienceUris>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="edad9-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="edad9-140">Identyfikator URI poszczególnych dodawane do kolekcji jest reprezentowany przez <xref:System.IdentityModel.Configuration.AudienceUriElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="edad9-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edad9-141">Korzystanie z `<audienceUris>` element jako element podrzędny [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu jest przestarzałe, ale nadal jest obsługiwany dla zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="edad9-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="edad9-142">Ustawienia na `<securityTokenHandlerConfiguration>` elemencie przesłaniają akcje na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="edad9-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edad9-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="edad9-143">Example</span></span>  
 <span data-ttu-id="edad9-144">Następujący kod XML przedstawia sposób konfigurowania odbiorców dopuszczalne identyfikatorów URI dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edad9-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="edad9-145">Ten przykład umożliwia skonfigurowanie pojedynczego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="edad9-145">This example configures a single URI.</span></span> <span data-ttu-id="edad9-146">Akceptowane są tokeny zakresu dla tego identyfikatora URI, wszystkie pozostałe zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="edad9-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
