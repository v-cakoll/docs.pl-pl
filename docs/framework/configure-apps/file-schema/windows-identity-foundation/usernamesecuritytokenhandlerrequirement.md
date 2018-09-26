---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: dfcaad8b150321fda2a86e601bf57204cbdc1a0e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216019"
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="42ab5-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="42ab5-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="42ab5-103">Udostępnia konfigurację dla <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="42ab5-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="42ab5-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="42ab5-104">\<system.identityModel></span></span>  
<span data-ttu-id="42ab5-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="42ab5-105">\<identityConfiguration></span></span>  
<span data-ttu-id="42ab5-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="42ab5-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="42ab5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="42ab5-107">\<add></span></span>  
<span data-ttu-id="42ab5-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="42ab5-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42ab5-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="42ab5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42ab5-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="42ab5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="42ab5-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="42ab5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42ab5-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="42ab5-112">Attributes</span></span>  
  
|<span data-ttu-id="42ab5-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="42ab5-113">Attribute</span></span>|<span data-ttu-id="42ab5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="42ab5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42ab5-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="42ab5-115">membershipProviderName</span></span>|<span data-ttu-id="42ab5-116">Określa <xref:System.Web.Security.MembershipProvider> , powinny być używane przez programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="42ab5-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42ab5-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="42ab5-117">Child Elements</span></span>  
 <span data-ttu-id="42ab5-118">Brak</span><span class="sxs-lookup"><span data-stu-id="42ab5-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42ab5-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="42ab5-119">Parent Elements</span></span>  
  
|<span data-ttu-id="42ab5-120">Element</span><span class="sxs-lookup"><span data-stu-id="42ab5-120">Element</span></span>|<span data-ttu-id="42ab5-121">Opis</span><span class="sxs-lookup"><span data-stu-id="42ab5-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42ab5-122">\<add></span><span class="sxs-lookup"><span data-stu-id="42ab5-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="42ab5-123">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="42ab5-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42ab5-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42ab5-124">Remarks</span></span>  
 <span data-ttu-id="42ab5-125">`<userNameSecurityTokenHandlerRequirement>` Ustawia element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> właściwości podczas <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="42ab5-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42ab5-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="42ab5-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
