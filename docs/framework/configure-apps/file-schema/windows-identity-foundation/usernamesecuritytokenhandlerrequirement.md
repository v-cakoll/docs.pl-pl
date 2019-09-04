---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251745"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="f0529-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="f0529-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="f0529-102">Zapewnia konfigurację <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f0529-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="f0529-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0529-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0529-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f0529-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f0529-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f0529-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f0529-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f0529-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f0529-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="f0529-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="f0529-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameSecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="f0529-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0529-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0529-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0529-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0529-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0529-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f0529-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0529-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0529-112">Attributes</span></span>  
  
|<span data-ttu-id="f0529-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f0529-113">Attribute</span></span>|<span data-ttu-id="f0529-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f0529-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0529-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="f0529-115">membershipProviderName</span></span>|<span data-ttu-id="f0529-116"><xref:System.Web.Security.MembershipProvider> Określa, który ma być używany przez program obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="f0529-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0529-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0529-117">Child Elements</span></span>  
 <span data-ttu-id="f0529-118">Brak</span><span class="sxs-lookup"><span data-stu-id="f0529-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0529-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0529-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f0529-120">Element</span><span class="sxs-lookup"><span data-stu-id="f0529-120">Element</span></span>|<span data-ttu-id="f0529-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f0529-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0529-122">\<add></span><span class="sxs-lookup"><span data-stu-id="f0529-122">\<add></span></span>](add.md)|<span data-ttu-id="f0529-123">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f0529-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0529-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0529-124">Remarks</span></span>  
 <span data-ttu-id="f0529-125">Element ustawia właściwość, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> gdy <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt jest inicjowany z konfiguracji. `<userNameSecurityTokenHandlerRequirement>`</span><span class="sxs-lookup"><span data-stu-id="f0529-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0529-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0529-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
