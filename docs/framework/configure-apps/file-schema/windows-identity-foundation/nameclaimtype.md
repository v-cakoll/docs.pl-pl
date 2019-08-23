---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942618"
---
# <a name="nameclaimtype"></a><span data-ttu-id="e8b49-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="e8b49-101">\<nameClaimType></span></span>
<span data-ttu-id="e8b49-102">Ustawia typ zgłoszenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="e8b49-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e8b49-103">Typ zgłoszenia służy do wyszukiwania <xref:System.Security.Claims.Claim> w <xref:System.Security.Claims.ClaimsIdentity> kolekcji obiektów zwracanych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e8b49-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="e8b49-104">Wartość zgodnego żądania jest następnie ustawiana jako nazwa <xref:System.Security.Principal.IIdentity> wygenerowanej na podstawie tej procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="e8b49-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="e8b49-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e8b49-105">\<system.identityModel></span></span>  
<span data-ttu-id="e8b49-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e8b49-106">\<identityConfiguration></span></span>  
<span data-ttu-id="e8b49-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e8b49-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e8b49-108">\<add></span><span class="sxs-lookup"><span data-stu-id="e8b49-108">\<add></span></span>  
<span data-ttu-id="e8b49-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e8b49-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="e8b49-110">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="e8b49-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b49-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8b49-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e8b49-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e8b49-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e8b49-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e8b49-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e8b49-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e8b49-114">Attributes</span></span>  
  
|<span data-ttu-id="e8b49-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e8b49-115">Attribute</span></span>|<span data-ttu-id="e8b49-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b49-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e8b49-117">value</span><span class="sxs-lookup"><span data-stu-id="e8b49-117">value</span></span>|<span data-ttu-id="e8b49-118">Ciąg określający identyfikator URI, który reprezentuje typ zgłoszenia do użycia dla <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e8b49-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e8b49-119">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e8b49-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e8b49-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e8b49-120">Child Elements</span></span>  
 <span data-ttu-id="e8b49-121">Brak</span><span class="sxs-lookup"><span data-stu-id="e8b49-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e8b49-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e8b49-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e8b49-123">Element</span><span class="sxs-lookup"><span data-stu-id="e8b49-123">Element</span></span>|<span data-ttu-id="e8b49-124">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b49-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e8b49-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e8b49-125">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="e8b49-126">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="e8b49-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8b49-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8b49-127">Remarks</span></span>  
 <span data-ttu-id="e8b49-128">Element ustawia właściwość, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> gdy <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji. `<nameClaimType>`</span><span class="sxs-lookup"><span data-stu-id="e8b49-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b49-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8b49-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8b49-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8b49-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
