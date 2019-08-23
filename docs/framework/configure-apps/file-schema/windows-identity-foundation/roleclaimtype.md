---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942542"
---
# <a name="roleclaimtype"></a><span data-ttu-id="aded1-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="aded1-101">\<roleClaimType></span></span>
<span data-ttu-id="aded1-102">Określa typ oświadczenia, który definiuje oświadczenia typu roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> przez metodę procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="aded1-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="aded1-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="aded1-103">\<system.identityModel></span></span>  
<span data-ttu-id="aded1-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="aded1-104">\<identityConfiguration></span></span>  
<span data-ttu-id="aded1-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="aded1-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="aded1-106">\<add></span><span class="sxs-lookup"><span data-stu-id="aded1-106">\<add></span></span>  
<span data-ttu-id="aded1-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="aded1-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="aded1-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="aded1-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aded1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="aded1-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aded1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="aded1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="aded1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="aded1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aded1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="aded1-112">Attributes</span></span>  
  
|<span data-ttu-id="aded1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="aded1-113">Attribute</span></span>|<span data-ttu-id="aded1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="aded1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aded1-115">value</span><span class="sxs-lookup"><span data-stu-id="aded1-115">value</span></span>|<span data-ttu-id="aded1-116">Ciąg określający identyfikator URI, który reprezentuje typ zgłoszenia do użycia dla typu roli.</span><span class="sxs-lookup"><span data-stu-id="aded1-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aded1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="aded1-117">Child Elements</span></span>  
 <span data-ttu-id="aded1-118">Brak</span><span class="sxs-lookup"><span data-stu-id="aded1-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aded1-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="aded1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="aded1-120">Element</span><span class="sxs-lookup"><span data-stu-id="aded1-120">Element</span></span>|<span data-ttu-id="aded1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="aded1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aded1-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="aded1-122">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="aded1-123">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="aded1-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aded1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aded1-124">Remarks</span></span>  
 <span data-ttu-id="aded1-125">Element ustawia właściwość, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> gdy <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji. `<roleClaimType>`</span><span class="sxs-lookup"><span data-stu-id="aded1-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aded1-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="aded1-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aded1-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aded1-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
