---
title: '&lt;sessionTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5a141dd83cb7ef1271906871097eb68da174d22f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="b6cf6-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="b6cf6-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="b6cf6-103">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="b6cf6-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="b6cf6-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="b6cf6-104">\<system.identityModel></span></span>  
<span data-ttu-id="b6cf6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="b6cf6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b6cf6-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="b6cf6-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="b6cf6-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="b6cf6-107">\<add></span></span>  
<span data-ttu-id="b6cf6-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="b6cf6-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6cf6-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6cf6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6cf6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b6cf6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6cf6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b6cf6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6cf6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b6cf6-112">Attributes</span></span>  
  
|<span data-ttu-id="b6cf6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b6cf6-113">Attribute</span></span>|<span data-ttu-id="b6cf6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b6cf6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6cf6-115">cykl życia</span><span class="sxs-lookup"><span data-stu-id="b6cf6-115">lifetime</span></span>|<span data-ttu-id="b6cf6-116">Określa okres istnienia tokenów sesji.</span><span class="sxs-lookup"><span data-stu-id="b6cf6-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6cf6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b6cf6-117">Child Elements</span></span>  
 <span data-ttu-id="b6cf6-118">Brak</span><span class="sxs-lookup"><span data-stu-id="b6cf6-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b6cf6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b6cf6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b6cf6-120">Element</span><span class="sxs-lookup"><span data-stu-id="b6cf6-120">Element</span></span>|<span data-ttu-id="b6cf6-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b6cf6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6cf6-122">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="b6cf6-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="b6cf6-123">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="b6cf6-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b6cf6-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6cf6-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
