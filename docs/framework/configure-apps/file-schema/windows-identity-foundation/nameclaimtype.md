---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e403667f16e316004f766b8476e20eca9bd1c988
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755100"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="a62fe-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="a62fe-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="a62fe-103">Ustawia typ oświadczenia, która określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a62fe-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="a62fe-104">Typ oświadczenia jest używana do wyszukania <xref:System.Security.Claims.Claim> w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiekty zwrócone przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="a62fe-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="a62fe-105">Następnie ustawionej wartości zgodne oświadczenie jako nazwa <xref:System.Security.Principal.IIdentity> generowane na podstawie tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="a62fe-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="a62fe-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a62fe-106">\<system.identityModel></span></span>  
<span data-ttu-id="a62fe-107">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a62fe-107">\<identityConfiguration></span></span>  
<span data-ttu-id="a62fe-108">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a62fe-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a62fe-109">\<add></span><span class="sxs-lookup"><span data-stu-id="a62fe-109">\<add></span></span>  
<span data-ttu-id="a62fe-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="a62fe-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="a62fe-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="a62fe-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62fe-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="a62fe-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a62fe-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a62fe-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a62fe-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a62fe-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a62fe-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a62fe-115">Attributes</span></span>  
  
|<span data-ttu-id="a62fe-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a62fe-116">Attribute</span></span>|<span data-ttu-id="a62fe-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a62fe-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a62fe-118">value</span><span class="sxs-lookup"><span data-stu-id="a62fe-118">value</span></span>|<span data-ttu-id="a62fe-119">Ciąg określający URI, który reprezentuje typ oświadczenia oświadczenia do użycia na potrzeby <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a62fe-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="a62fe-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="a62fe-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a62fe-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a62fe-121">Child Elements</span></span>  
 <span data-ttu-id="a62fe-122">Brak</span><span class="sxs-lookup"><span data-stu-id="a62fe-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a62fe-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a62fe-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a62fe-124">Element</span><span class="sxs-lookup"><span data-stu-id="a62fe-124">Element</span></span>|<span data-ttu-id="a62fe-125">Opis</span><span class="sxs-lookup"><span data-stu-id="a62fe-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a62fe-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="a62fe-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="a62fe-127">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej każdej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="a62fe-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a62fe-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a62fe-128">Remarks</span></span>  
 <span data-ttu-id="a62fe-129">`<nameClaimType>` Ustawia element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> właściwości podczas <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt został zainicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a62fe-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a62fe-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="a62fe-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a62fe-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a62fe-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
