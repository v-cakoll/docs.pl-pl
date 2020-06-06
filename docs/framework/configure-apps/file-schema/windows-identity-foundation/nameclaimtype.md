---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251939"
---
# \<nameClaimType>
<span data-ttu-id="054fa-101">Ustawia typ zgłoszenia, który określa <xref:System.Security.Principal.IIdentity.Name%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="054fa-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="054fa-102">Typ zgłoszenia służy do wyszukiwania <xref:System.Security.Claims.Claim> w kolekcji <xref:System.Security.Claims.ClaimsIdentity> obiektów zwracanych przez <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodę tego programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="054fa-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="054fa-103">Wartość zgodnego żądania jest następnie ustawiana jako nazwa <xref:System.Security.Principal.IIdentity> wygenerowanej na podstawie tej procedury obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="054fa-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="054fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="054fa-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="054fa-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="054fa-105">Attributes and Elements</span></span>  
 <span data-ttu-id="054fa-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="054fa-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="054fa-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="054fa-107">Attributes</span></span>  
  
|<span data-ttu-id="054fa-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="054fa-108">Attribute</span></span>|<span data-ttu-id="054fa-109">Opis</span><span class="sxs-lookup"><span data-stu-id="054fa-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="054fa-110">value</span><span class="sxs-lookup"><span data-stu-id="054fa-110">value</span></span>|<span data-ttu-id="054fa-111">Ciąg określający identyfikator URI, który reprezentuje typ zgłoszenia do użycia dla <xref:System.Security.Principal.IIdentity.Name%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="054fa-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="054fa-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="054fa-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="054fa-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="054fa-113">Child Elements</span></span>  
 <span data-ttu-id="054fa-114">Brak</span><span class="sxs-lookup"><span data-stu-id="054fa-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="054fa-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="054fa-115">Parent Elements</span></span>  
  
|<span data-ttu-id="054fa-116">Element</span><span class="sxs-lookup"><span data-stu-id="054fa-116">Element</span></span>|<span data-ttu-id="054fa-117">Opis</span><span class="sxs-lookup"><span data-stu-id="054fa-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="054fa-118">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> klasy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> klasy lub klasy pochodnej jednej z tych klas.</span><span class="sxs-lookup"><span data-stu-id="054fa-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="054fa-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="054fa-119">Remarks</span></span>  
 <span data-ttu-id="054fa-120">`<nameClaimType>`Element ustawia właściwość, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> gdy <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="054fa-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="054fa-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="054fa-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="054fa-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="054fa-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
