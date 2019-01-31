---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271892"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="25740-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="25740-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="25740-102">Udostępnia konfigurację dla <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="25740-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="25740-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="25740-103">\<system.identityModel></span></span>  
<span data-ttu-id="25740-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="25740-104">\<identityConfiguration></span></span>  
<span data-ttu-id="25740-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="25740-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="25740-106">\<add></span><span class="sxs-lookup"><span data-stu-id="25740-106">\<add></span></span>  
<span data-ttu-id="25740-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="25740-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25740-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="25740-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25740-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25740-109">Attributes and Elements</span></span>  
 <span data-ttu-id="25740-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25740-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25740-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25740-111">Attributes</span></span>  
  
|<span data-ttu-id="25740-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="25740-112">Attribute</span></span>|<span data-ttu-id="25740-113">Opis</span><span class="sxs-lookup"><span data-stu-id="25740-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="25740-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="25740-114">membershipProviderName</span></span>|<span data-ttu-id="25740-115">Określa <xref:System.Web.Security.MembershipProvider> , powinny być używane przez programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="25740-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25740-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25740-116">Child Elements</span></span>  
 <span data-ttu-id="25740-117">Brak</span><span class="sxs-lookup"><span data-stu-id="25740-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25740-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25740-118">Parent Elements</span></span>  
  
|<span data-ttu-id="25740-119">Element</span><span class="sxs-lookup"><span data-stu-id="25740-119">Element</span></span>|<span data-ttu-id="25740-120">Opis</span><span class="sxs-lookup"><span data-stu-id="25740-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25740-121">\<add></span><span class="sxs-lookup"><span data-stu-id="25740-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="25740-122">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="25740-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25740-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25740-123">Remarks</span></span>  
 <span data-ttu-id="25740-124">`<userNameSecurityTokenHandlerRequirement>` Ustawia element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> właściwości podczas <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="25740-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25740-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="25740-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
