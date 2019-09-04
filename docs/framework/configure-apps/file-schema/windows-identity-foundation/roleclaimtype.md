---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251912"
---
# <a name="roleclaimtype"></a><span data-ttu-id="5fa55-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="5fa55-101">\<roleClaimType></span></span>
<span data-ttu-id="5fa55-102">Określa typ oświadczenia, który definiuje oświadczenia typu roli w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> przez metodę procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="5fa55-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
<span data-ttu-id="5fa55-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5fa55-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5fa55-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="5fa55-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="5fa55-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="5fa55-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="5fa55-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="5fa55-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="5fa55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="5fa55-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="5fa55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="5fa55-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="5fa55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<roleClaimType >**</span><span class="sxs-lookup"><span data-stu-id="5fa55-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa55-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="5fa55-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fa55-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5fa55-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5fa55-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5fa55-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fa55-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5fa55-113">Attributes</span></span>  
  
|<span data-ttu-id="5fa55-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="5fa55-114">Attribute</span></span>|<span data-ttu-id="5fa55-115">Opis</span><span class="sxs-lookup"><span data-stu-id="5fa55-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fa55-116">value</span><span class="sxs-lookup"><span data-stu-id="5fa55-116">value</span></span>|<span data-ttu-id="5fa55-117">Ciąg określający identyfikator URI, który reprezentuje typ zgłoszenia do użycia dla typu roli.</span><span class="sxs-lookup"><span data-stu-id="5fa55-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fa55-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5fa55-118">Child Elements</span></span>  
 <span data-ttu-id="5fa55-119">Brak</span><span class="sxs-lookup"><span data-stu-id="5fa55-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fa55-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5fa55-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5fa55-121">Element</span><span class="sxs-lookup"><span data-stu-id="5fa55-121">Element</span></span>|<span data-ttu-id="5fa55-122">Opis</span><span class="sxs-lookup"><span data-stu-id="5fa55-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fa55-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5fa55-123">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="5fa55-124">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="5fa55-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fa55-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5fa55-125">Remarks</span></span>  
 <span data-ttu-id="5fa55-126">Element ustawia właściwość, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> gdy <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji. `<roleClaimType>`</span><span class="sxs-lookup"><span data-stu-id="5fa55-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa55-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fa55-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5fa55-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fa55-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
