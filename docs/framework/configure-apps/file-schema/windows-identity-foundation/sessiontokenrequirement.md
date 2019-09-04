---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 968c48df9e92a1dfbfb6e248b06cf4f97cece8b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251816"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="2a40e-101">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2a40e-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="2a40e-102">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="2a40e-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="2a40e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a40e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a40e-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="2a40e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="2a40e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="2a40e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="2a40e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="2a40e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="2a40e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Dodaj >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="2a40e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="2a40e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="2a40e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a40e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a40e-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a40e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2a40e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a40e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2a40e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a40e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2a40e-112">Attributes</span></span>  
  
|<span data-ttu-id="2a40e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2a40e-113">Attribute</span></span>|<span data-ttu-id="2a40e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2a40e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a40e-115">cykl życia</span><span class="sxs-lookup"><span data-stu-id="2a40e-115">lifetime</span></span>|<span data-ttu-id="2a40e-116">Określa okres istnienia tokenów sesji.</span><span class="sxs-lookup"><span data-stu-id="2a40e-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a40e-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2a40e-117">Child Elements</span></span>  
 <span data-ttu-id="2a40e-118">Brak</span><span class="sxs-lookup"><span data-stu-id="2a40e-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a40e-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2a40e-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2a40e-120">Element</span><span class="sxs-lookup"><span data-stu-id="2a40e-120">Element</span></span>|<span data-ttu-id="2a40e-121">Opis</span><span class="sxs-lookup"><span data-stu-id="2a40e-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a40e-122">\<add></span><span class="sxs-lookup"><span data-stu-id="2a40e-122">\<add></span></span>](add.md)|<span data-ttu-id="2a40e-123">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="2a40e-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a40e-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a40e-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
