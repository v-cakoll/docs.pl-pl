---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6c40948633eaf892db06e9bba756158dfc3c4a2e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754993"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="b6d00-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="b6d00-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="b6d00-103">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b6d00-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="b6d00-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b6d00-104">\<system.identityModel></span></span>  
<span data-ttu-id="b6d00-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b6d00-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b6d00-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="b6d00-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b6d00-107">\<add></span><span class="sxs-lookup"><span data-stu-id="b6d00-107">\<add></span></span>  
<span data-ttu-id="b6d00-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="b6d00-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d00-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6d00-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6d00-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6d00-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6d00-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6d00-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6d00-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6d00-112">Attributes</span></span>  
  
|<span data-ttu-id="b6d00-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6d00-113">Attribute</span></span>|<span data-ttu-id="b6d00-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b6d00-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6d00-115">cykl życia</span><span class="sxs-lookup"><span data-stu-id="b6d00-115">lifetime</span></span>|<span data-ttu-id="b6d00-116">Określa okres istnienia tokenów sesji.</span><span class="sxs-lookup"><span data-stu-id="b6d00-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6d00-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6d00-117">Child Elements</span></span>  
 <span data-ttu-id="b6d00-118">Brak</span><span class="sxs-lookup"><span data-stu-id="b6d00-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6d00-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6d00-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b6d00-120">Element</span><span class="sxs-lookup"><span data-stu-id="b6d00-120">Element</span></span>|<span data-ttu-id="b6d00-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b6d00-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6d00-122">\<add></span><span class="sxs-lookup"><span data-stu-id="b6d00-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b6d00-123">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b6d00-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6d00-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6d00-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
