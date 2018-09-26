---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4d5d2348f04ace7596a3a513c5106ea612dc17b7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070095"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="2de6e-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="2de6e-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="2de6e-103">Udostępnia konfigurację dla <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="2de6e-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="2de6e-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2de6e-104">\<system.identityModel></span></span>  
<span data-ttu-id="2de6e-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2de6e-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2de6e-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2de6e-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2de6e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="2de6e-107">\<add></span></span>  
<span data-ttu-id="2de6e-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2de6e-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2de6e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2de6e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2de6e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2de6e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2de6e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2de6e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2de6e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2de6e-112">Attributes</span></span>  
  
|<span data-ttu-id="2de6e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2de6e-113">Attribute</span></span>|<span data-ttu-id="2de6e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2de6e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2de6e-115">cykl życia</span><span class="sxs-lookup"><span data-stu-id="2de6e-115">lifetime</span></span>|<span data-ttu-id="2de6e-116">Określa okres istnienia tokenów, sesji.</span><span class="sxs-lookup"><span data-stu-id="2de6e-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2de6e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2de6e-117">Child Elements</span></span>  
 <span data-ttu-id="2de6e-118">Brak</span><span class="sxs-lookup"><span data-stu-id="2de6e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2de6e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2de6e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2de6e-120">Element</span><span class="sxs-lookup"><span data-stu-id="2de6e-120">Element</span></span>|<span data-ttu-id="2de6e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2de6e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2de6e-122">\<add></span><span class="sxs-lookup"><span data-stu-id="2de6e-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="2de6e-123">Programu obsługi tokenów zabezpieczeń określone są dodawane do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="2de6e-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2de6e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2de6e-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
