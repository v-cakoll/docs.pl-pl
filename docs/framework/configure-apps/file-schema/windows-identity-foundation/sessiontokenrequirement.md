---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152544"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="d4e20-101">\<sessionTokenOkiwki></span><span class="sxs-lookup"><span data-stu-id="d4e20-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="d4e20-102">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> dla klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="d4e20-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="d4e20-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d4e20-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d4e20-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d4e20-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d4e20-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d4e20-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d4e20-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d4e20-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d4e20-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dodaj>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="d4e20-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="d4e20-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenOkiwki>**</span><span class="sxs-lookup"><span data-stu-id="d4e20-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e20-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4e20-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4e20-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d4e20-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4e20-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d4e20-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4e20-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d4e20-112">Attributes</span></span>  
  
|<span data-ttu-id="d4e20-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d4e20-113">Attribute</span></span>|<span data-ttu-id="d4e20-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e20-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4e20-115">cykl życia</span><span class="sxs-lookup"><span data-stu-id="d4e20-115">lifetime</span></span>|<span data-ttu-id="d4e20-116">Określa okres istnienia tokenów sesji.</span><span class="sxs-lookup"><span data-stu-id="d4e20-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4e20-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d4e20-117">Child Elements</span></span>  
 <span data-ttu-id="d4e20-118">Brak</span><span class="sxs-lookup"><span data-stu-id="d4e20-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4e20-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d4e20-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d4e20-120">Element</span><span class="sxs-lookup"><span data-stu-id="d4e20-120">Element</span></span>|<span data-ttu-id="d4e20-121">Opis</span><span class="sxs-lookup"><span data-stu-id="d4e20-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4e20-122">\<dodaj></span><span class="sxs-lookup"><span data-stu-id="d4e20-122">\<add></span></span>](add.md)|<span data-ttu-id="d4e20-123">Dodaje określony program obsługi tokenu zabezpieczającego do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="d4e20-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4e20-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4e20-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
