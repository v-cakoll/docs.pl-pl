---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: bd4033b2edea7450b66c25f446669b3ded65e9af
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459833"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="918b5-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="918b5-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="918b5-103">Ustawia typ oświadczenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="918b5-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="918b5-104">Typ oświadczenia jest używany do wyszukiwania <xref:System.Security.Claims.Claim> w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwróconych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metody tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="918b5-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="918b5-105">Zgodne oświadczenie jest następnie wartość jako nazwa <xref:System.Security.Principal.IIdentity> wygenerowany na podstawie tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="918b5-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="918b5-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="918b5-106">\<system.identityModel></span></span>  
<span data-ttu-id="918b5-107">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="918b5-107">\<identityConfiguration></span></span>  
<span data-ttu-id="918b5-108">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="918b5-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="918b5-109">\<add></span><span class="sxs-lookup"><span data-stu-id="918b5-109">\<add></span></span>  
<span data-ttu-id="918b5-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="918b5-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="918b5-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="918b5-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="918b5-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="918b5-112">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="918b5-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="918b5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="918b5-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="918b5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="918b5-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="918b5-115">Attributes</span></span>  
  
|<span data-ttu-id="918b5-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="918b5-116">Attribute</span></span>|<span data-ttu-id="918b5-117">Opis</span><span class="sxs-lookup"><span data-stu-id="918b5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="918b5-118">value</span><span class="sxs-lookup"><span data-stu-id="918b5-118">value</span></span>|<span data-ttu-id="918b5-119">Ciąg określający URI, który reprezentuje typ oświadczenia, oświadczenia do użycia dla <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="918b5-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="918b5-120">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="918b5-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="918b5-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="918b5-121">Child Elements</span></span>  
 <span data-ttu-id="918b5-122">Brak</span><span class="sxs-lookup"><span data-stu-id="918b5-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="918b5-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="918b5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="918b5-124">Element</span><span class="sxs-lookup"><span data-stu-id="918b5-124">Element</span></span>|<span data-ttu-id="918b5-125">Opis</span><span class="sxs-lookup"><span data-stu-id="918b5-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="918b5-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="918b5-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="918b5-127">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="918b5-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="918b5-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="918b5-128">Remarks</span></span>  
 <span data-ttu-id="918b5-129">`<nameClaimType>` Ustawia element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> właściwości podczas <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="918b5-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="918b5-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="918b5-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="918b5-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="918b5-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
