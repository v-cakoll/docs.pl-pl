---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: fed8964e03b80e365fdc5eafd45b4fc372a6e352
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944250"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="3243e-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="3243e-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="3243e-102">Zapewnia konfigurację <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="3243e-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="3243e-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3243e-103">\<system.identityModel></span></span>  
<span data-ttu-id="3243e-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3243e-104">\<identityConfiguration></span></span>  
<span data-ttu-id="3243e-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="3243e-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3243e-106">\<add></span><span class="sxs-lookup"><span data-stu-id="3243e-106">\<add></span></span>  
<span data-ttu-id="3243e-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="3243e-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3243e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3243e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3243e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3243e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3243e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3243e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3243e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3243e-111">Attributes</span></span>  
  
|<span data-ttu-id="3243e-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3243e-112">Attribute</span></span>|<span data-ttu-id="3243e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3243e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3243e-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="3243e-114">membershipProviderName</span></span>|<span data-ttu-id="3243e-115"><xref:System.Web.Security.MembershipProvider> Określa, który ma być używany przez program obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="3243e-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3243e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3243e-116">Child Elements</span></span>  
 <span data-ttu-id="3243e-117">Brak</span><span class="sxs-lookup"><span data-stu-id="3243e-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3243e-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3243e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3243e-119">Element</span><span class="sxs-lookup"><span data-stu-id="3243e-119">Element</span></span>|<span data-ttu-id="3243e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3243e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3243e-121">\<add></span><span class="sxs-lookup"><span data-stu-id="3243e-121">\<add></span></span>](add.md)|<span data-ttu-id="3243e-122">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="3243e-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3243e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3243e-123">Remarks</span></span>  
 <span data-ttu-id="3243e-124">Element ustawia właściwość, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> gdy <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt jest inicjowany z konfiguracji. `<userNameSecurityTokenHandlerRequirement>`</span><span class="sxs-lookup"><span data-stu-id="3243e-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3243e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3243e-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
