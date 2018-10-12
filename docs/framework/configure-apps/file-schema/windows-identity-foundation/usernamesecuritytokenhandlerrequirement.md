---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: dfcaad8b150321fda2a86e601bf57204cbdc1a0e
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123387"
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="e1ccb-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="e1ccb-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="e1ccb-103">Udostępnia konfigurację dla <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="e1ccb-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="e1ccb-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e1ccb-104">\<system.identityModel></span></span>  
<span data-ttu-id="e1ccb-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e1ccb-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e1ccb-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e1ccb-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e1ccb-107">\<add></span><span class="sxs-lookup"><span data-stu-id="e1ccb-107">\<add></span></span>  
<span data-ttu-id="e1ccb-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="e1ccb-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1ccb-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1ccb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1ccb-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1ccb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e1ccb-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1ccb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1ccb-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1ccb-112">Attributes</span></span>  
  
|<span data-ttu-id="e1ccb-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e1ccb-113">Attribute</span></span>|<span data-ttu-id="e1ccb-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e1ccb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1ccb-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="e1ccb-115">membershipProviderName</span></span>|<span data-ttu-id="e1ccb-116">Określa <xref:System.Web.Security.MembershipProvider> , powinny być używane przez programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="e1ccb-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1ccb-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1ccb-117">Child Elements</span></span>  
 <span data-ttu-id="e1ccb-118">Brak</span><span class="sxs-lookup"><span data-stu-id="e1ccb-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1ccb-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1ccb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e1ccb-120">Element</span><span class="sxs-lookup"><span data-stu-id="e1ccb-120">Element</span></span>|<span data-ttu-id="e1ccb-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e1ccb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1ccb-122">\<add></span><span class="sxs-lookup"><span data-stu-id="e1ccb-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="e1ccb-123">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e1ccb-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1ccb-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1ccb-124">Remarks</span></span>  
 <span data-ttu-id="e1ccb-125">`<userNameSecurityTokenHandlerRequirement>` Ustawia element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> właściwości podczas <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e1ccb-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1ccb-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1ccb-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
