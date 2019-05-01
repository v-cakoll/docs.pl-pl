---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793773"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="1fabb-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="1fabb-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="1fabb-102">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="1fabb-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="1fabb-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1fabb-103">\<system.identityModel></span></span>  
<span data-ttu-id="1fabb-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1fabb-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1fabb-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1fabb-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1fabb-106">\<add></span><span class="sxs-lookup"><span data-stu-id="1fabb-106">\<add></span></span>  
<span data-ttu-id="1fabb-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="1fabb-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fabb-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fabb-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fabb-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fabb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1fabb-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fabb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fabb-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fabb-111">Attributes</span></span>  
  
|<span data-ttu-id="1fabb-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1fabb-112">Attribute</span></span>|<span data-ttu-id="1fabb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="1fabb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1fabb-114">cykl życia</span><span class="sxs-lookup"><span data-stu-id="1fabb-114">lifetime</span></span>|<span data-ttu-id="1fabb-115">Określa okres istnienia tokenów, sesji.</span><span class="sxs-lookup"><span data-stu-id="1fabb-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fabb-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fabb-116">Child Elements</span></span>  
 <span data-ttu-id="1fabb-117">Brak</span><span class="sxs-lookup"><span data-stu-id="1fabb-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fabb-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fabb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1fabb-119">Element</span><span class="sxs-lookup"><span data-stu-id="1fabb-119">Element</span></span>|<span data-ttu-id="1fabb-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1fabb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fabb-121">\<add></span><span class="sxs-lookup"><span data-stu-id="1fabb-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="1fabb-122">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="1fabb-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1fabb-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fabb-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
