---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 254d34149892abeaf31b9227f7567eb0a66ec0b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943674"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="f8cd3-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f8cd3-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="f8cd3-102">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f8cd3-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="f8cd3-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f8cd3-103">\<system.identityModel></span></span>  
<span data-ttu-id="f8cd3-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f8cd3-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f8cd3-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f8cd3-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f8cd3-106">\<add></span><span class="sxs-lookup"><span data-stu-id="f8cd3-106">\<add></span></span>  
<span data-ttu-id="f8cd3-107">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f8cd3-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8cd3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8cd3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8cd3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f8cd3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f8cd3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f8cd3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8cd3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f8cd3-111">Attributes</span></span>  
  
|<span data-ttu-id="f8cd3-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f8cd3-112">Attribute</span></span>|<span data-ttu-id="f8cd3-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f8cd3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8cd3-114">cykl życia</span><span class="sxs-lookup"><span data-stu-id="f8cd3-114">lifetime</span></span>|<span data-ttu-id="f8cd3-115">Określa okres istnienia tokenów sesji.</span><span class="sxs-lookup"><span data-stu-id="f8cd3-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8cd3-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f8cd3-116">Child Elements</span></span>  
 <span data-ttu-id="f8cd3-117">Brak</span><span class="sxs-lookup"><span data-stu-id="f8cd3-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8cd3-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f8cd3-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f8cd3-119">Element</span><span class="sxs-lookup"><span data-stu-id="f8cd3-119">Element</span></span>|<span data-ttu-id="f8cd3-120">Opis</span><span class="sxs-lookup"><span data-stu-id="f8cd3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8cd3-121">\<add></span><span class="sxs-lookup"><span data-stu-id="f8cd3-121">\<add></span></span>](add.md)|<span data-ttu-id="f8cd3-122">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="f8cd3-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f8cd3-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8cd3-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
