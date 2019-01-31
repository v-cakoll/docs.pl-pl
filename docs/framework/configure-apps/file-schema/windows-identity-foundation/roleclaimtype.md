---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 812d44ef947d27b0f73d9dc2172494e89ee56d72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270878"
---
# <a name="roleclaimtype"></a><span data-ttu-id="3e1b5-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="3e1b5-101">\<roleClaimType></span></span>
<span data-ttu-id="3e1b5-102">Określa typ oświadczenia, który definiuje typ oświadczenia roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwróconych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="3e1b5-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3e1b5-103">\<system.identityModel></span></span>  
<span data-ttu-id="3e1b5-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3e1b5-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3e1b5-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="3e1b5-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3e1b5-106">\<add></span><span class="sxs-lookup"><span data-stu-id="3e1b5-106">\<add></span></span>  
<span data-ttu-id="3e1b5-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="3e1b5-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="3e1b5-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="3e1b5-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1b5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e1b5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e1b5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3e1b5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e1b5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e1b5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e1b5-112">Attributes</span></span>  
  
|<span data-ttu-id="3e1b5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3e1b5-113">Attribute</span></span>|<span data-ttu-id="3e1b5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3e1b5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e1b5-115">value</span><span class="sxs-lookup"><span data-stu-id="3e1b5-115">value</span></span>|<span data-ttu-id="3e1b5-116">Ciąg określający URI, który reprezentuje typ oświadczenia, oświadczenia do użycia typ oświadczenia roli.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e1b5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3e1b5-117">Child Elements</span></span>  
 <span data-ttu-id="3e1b5-118">Brak</span><span class="sxs-lookup"><span data-stu-id="3e1b5-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e1b5-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3e1b5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="3e1b5-120">Element</span><span class="sxs-lookup"><span data-stu-id="3e1b5-120">Element</span></span>|<span data-ttu-id="3e1b5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3e1b5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e1b5-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="3e1b5-122">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="3e1b5-123">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e1b5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e1b5-124">Remarks</span></span>  
 <span data-ttu-id="3e1b5-125">`<roleClaimType>` Ustawia element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> właściwości podczas <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e1b5-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e1b5-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e1b5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e1b5-127">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
