---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5d725cc0d16457f2bdfb404baf4758e3431ce6b7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32756660"
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="c5cf8-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="c5cf8-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="c5cf8-103">Zapewnia konfigurację <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="c5cf8-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="c5cf8-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c5cf8-104">\<system.identityModel></span></span>  
<span data-ttu-id="c5cf8-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c5cf8-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c5cf8-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="c5cf8-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c5cf8-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c5cf8-107">\<add></span></span>  
<span data-ttu-id="c5cf8-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="c5cf8-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5cf8-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5cf8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5cf8-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c5cf8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5cf8-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c5cf8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5cf8-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c5cf8-112">Attributes</span></span>  
  
|<span data-ttu-id="c5cf8-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c5cf8-113">Attribute</span></span>|<span data-ttu-id="c5cf8-114">Opis</span><span class="sxs-lookup"><span data-stu-id="c5cf8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5cf8-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="c5cf8-115">membershipProviderName</span></span>|<span data-ttu-id="c5cf8-116">Określa <xref:System.Web.Security.MembershipProvider> która powinna być używana przez program obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c5cf8-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5cf8-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c5cf8-117">Child Elements</span></span>  
 <span data-ttu-id="c5cf8-118">Brak</span><span class="sxs-lookup"><span data-stu-id="c5cf8-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5cf8-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c5cf8-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c5cf8-120">Element</span><span class="sxs-lookup"><span data-stu-id="c5cf8-120">Element</span></span>|<span data-ttu-id="c5cf8-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c5cf8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5cf8-122">\<add></span><span class="sxs-lookup"><span data-stu-id="c5cf8-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="c5cf8-123">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="c5cf8-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5cf8-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5cf8-124">Remarks</span></span>  
 <span data-ttu-id="c5cf8-125">`<userNameSecurityTokenHandlerRequirement>` Ustawia element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> właściwości podczas <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt został zainicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c5cf8-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5cf8-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5cf8-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
