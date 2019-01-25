---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 6114a95f3942c367849785ce981858f276c0b8fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599949"
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="0f0e2-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="0f0e2-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="0f0e2-103">Określa typ oświadczenia, który definiuje typ oświadczenia roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwróconych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="0f0e2-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="0f0e2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0f0e2-104">\<system.identityModel></span></span>  
<span data-ttu-id="0f0e2-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0f0e2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0f0e2-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0f0e2-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0f0e2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="0f0e2-107">\<add></span></span>  
<span data-ttu-id="0f0e2-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="0f0e2-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="0f0e2-109">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="0f0e2-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f0e2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f0e2-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f0e2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0f0e2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0f0e2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0f0e2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f0e2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0f0e2-113">Attributes</span></span>  
  
|<span data-ttu-id="0f0e2-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="0f0e2-114">Attribute</span></span>|<span data-ttu-id="0f0e2-115">Opis</span><span class="sxs-lookup"><span data-stu-id="0f0e2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f0e2-116">value</span><span class="sxs-lookup"><span data-stu-id="0f0e2-116">value</span></span>|<span data-ttu-id="0f0e2-117">Ciąg określający URI, który reprezentuje typ oświadczenia, oświadczenia do użycia typ oświadczenia roli.</span><span class="sxs-lookup"><span data-stu-id="0f0e2-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f0e2-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0f0e2-118">Child Elements</span></span>  
 <span data-ttu-id="0f0e2-119">Brak</span><span class="sxs-lookup"><span data-stu-id="0f0e2-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f0e2-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0f0e2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="0f0e2-121">Element</span><span class="sxs-lookup"><span data-stu-id="0f0e2-121">Element</span></span>|<span data-ttu-id="0f0e2-122">Opis</span><span class="sxs-lookup"><span data-stu-id="0f0e2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f0e2-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="0f0e2-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="0f0e2-124">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="0f0e2-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f0e2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f0e2-125">Remarks</span></span>  
 <span data-ttu-id="0f0e2-126">`<roleClaimType>` Ustawia element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> właściwości podczas <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0f0e2-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f0e2-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f0e2-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f0e2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f0e2-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
