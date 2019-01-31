---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: aab76949d9c31ac003b8afd519c2ad66529cbf26
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254867"
---
# <a name="nameclaimtype"></a><span data-ttu-id="86cef-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="86cef-101">\<nameClaimType></span></span>
<span data-ttu-id="86cef-102">Ustawia typ oświadczenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="86cef-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="86cef-103">Typ oświadczenia jest używany do wyszukiwania <xref:System.Security.Claims.Claim> w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwróconych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metody tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="86cef-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="86cef-104">Zgodne oświadczenie jest następnie wartość jako nazwa <xref:System.Security.Principal.IIdentity> wygenerowany na podstawie tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="86cef-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="86cef-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="86cef-105">\<system.identityModel></span></span>  
<span data-ttu-id="86cef-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="86cef-106">\<identityConfiguration></span></span>  
<span data-ttu-id="86cef-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="86cef-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="86cef-108">\<add></span><span class="sxs-lookup"><span data-stu-id="86cef-108">\<add></span></span>  
<span data-ttu-id="86cef-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="86cef-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="86cef-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="86cef-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cef-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="86cef-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86cef-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="86cef-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86cef-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="86cef-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86cef-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="86cef-114">Attributes</span></span>  
  
|<span data-ttu-id="86cef-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="86cef-115">Attribute</span></span>|<span data-ttu-id="86cef-116">Opis</span><span class="sxs-lookup"><span data-stu-id="86cef-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86cef-117">value</span><span class="sxs-lookup"><span data-stu-id="86cef-117">value</span></span>|<span data-ttu-id="86cef-118">Ciąg określający URI, który reprezentuje typ oświadczenia, oświadczenia do użycia dla <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="86cef-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="86cef-119">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="86cef-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86cef-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="86cef-120">Child Elements</span></span>  
 <span data-ttu-id="86cef-121">Brak</span><span class="sxs-lookup"><span data-stu-id="86cef-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86cef-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="86cef-122">Parent Elements</span></span>  
  
|<span data-ttu-id="86cef-123">Element</span><span class="sxs-lookup"><span data-stu-id="86cef-123">Element</span></span>|<span data-ttu-id="86cef-124">Opis</span><span class="sxs-lookup"><span data-stu-id="86cef-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86cef-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="86cef-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="86cef-126">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej z jednego z tych klas.</span><span class="sxs-lookup"><span data-stu-id="86cef-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86cef-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86cef-127">Remarks</span></span>  
 <span data-ttu-id="86cef-128">`<nameClaimType>` Ustawia element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> właściwości podczas <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="86cef-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86cef-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="86cef-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86cef-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86cef-130">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
