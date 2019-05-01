---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790458"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="acf49-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="acf49-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="acf49-102">Udostępnia konfigurację dla <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="acf49-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="acf49-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="acf49-103">\<system.identityModel></span></span>  
<span data-ttu-id="acf49-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="acf49-104">\<identityConfiguration></span></span>  
<span data-ttu-id="acf49-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="acf49-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="acf49-106">\<add></span><span class="sxs-lookup"><span data-stu-id="acf49-106">\<add></span></span>  
<span data-ttu-id="acf49-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="acf49-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acf49-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="acf49-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="acf49-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="acf49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="acf49-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="acf49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="acf49-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="acf49-111">Attributes</span></span>  
  
|<span data-ttu-id="acf49-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="acf49-112">Attribute</span></span>|<span data-ttu-id="acf49-113">Opis</span><span class="sxs-lookup"><span data-stu-id="acf49-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="acf49-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="acf49-114">membershipProviderName</span></span>|<span data-ttu-id="acf49-115">Określa <xref:System.Web.Security.MembershipProvider> , powinny być używane przez programu obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="acf49-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="acf49-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="acf49-116">Child Elements</span></span>  
 <span data-ttu-id="acf49-117">Brak</span><span class="sxs-lookup"><span data-stu-id="acf49-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="acf49-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="acf49-118">Parent Elements</span></span>  
  
|<span data-ttu-id="acf49-119">Element</span><span class="sxs-lookup"><span data-stu-id="acf49-119">Element</span></span>|<span data-ttu-id="acf49-120">Opis</span><span class="sxs-lookup"><span data-stu-id="acf49-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="acf49-121">\<add></span><span class="sxs-lookup"><span data-stu-id="acf49-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="acf49-122">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="acf49-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf49-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="acf49-123">Remarks</span></span>  
 <span data-ttu-id="acf49-124">`<userNameSecurityTokenHandlerRequirement>` Ustawia element <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> właściwości podczas <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> obiekt jest inicjowany z konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="acf49-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acf49-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="acf49-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
