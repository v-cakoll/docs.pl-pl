---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251939"
---
# <a name="nameclaimtype"></a><span data-ttu-id="e98b0-101">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="e98b0-101">\<nameClaimType></span></span>
<span data-ttu-id="e98b0-102">Ustawia typ zgłoszenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="e98b0-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e98b0-103">Typ zgłoszenia służy do wyszukiwania <xref:System.Security.Claims.Claim> w <xref:System.Security.Claims.ClaimsIdentity> kolekcji obiektów zwracanych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e98b0-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="e98b0-104">Wartość zgodnego żądania jest następnie ustawiana jako nazwa <xref:System.Security.Principal.IIdentity> wygenerowanej na podstawie tej procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="e98b0-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
<span data-ttu-id="e98b0-105">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e98b0-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e98b0-106">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e98b0-106">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e98b0-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e98b0-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e98b0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="e98b0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="e98b0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="e98b0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="e98b0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="e98b0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="e98b0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameClaimType >**</span><span class="sxs-lookup"><span data-stu-id="e98b0-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e98b0-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="e98b0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e98b0-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e98b0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e98b0-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e98b0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e98b0-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e98b0-115">Attributes</span></span>  
  
|<span data-ttu-id="e98b0-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e98b0-116">Attribute</span></span>|<span data-ttu-id="e98b0-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e98b0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e98b0-118">value</span><span class="sxs-lookup"><span data-stu-id="e98b0-118">value</span></span>|<span data-ttu-id="e98b0-119">Ciąg określający identyfikator URI, który reprezentuje typ zgłoszenia do użycia dla <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e98b0-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e98b0-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e98b0-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e98b0-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e98b0-121">Child Elements</span></span>  
 <span data-ttu-id="e98b0-122">Brak</span><span class="sxs-lookup"><span data-stu-id="e98b0-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e98b0-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e98b0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e98b0-124">Element</span><span class="sxs-lookup"><span data-stu-id="e98b0-124">Element</span></span>|<span data-ttu-id="e98b0-125">Opis</span><span class="sxs-lookup"><span data-stu-id="e98b0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e98b0-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e98b0-126">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="e98b0-127">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="e98b0-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e98b0-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e98b0-128">Remarks</span></span>  
 <span data-ttu-id="e98b0-129">Element ustawia właściwość, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> gdy <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji. `<nameClaimType>`</span><span class="sxs-lookup"><span data-stu-id="e98b0-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e98b0-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="e98b0-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e98b0-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e98b0-131">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
