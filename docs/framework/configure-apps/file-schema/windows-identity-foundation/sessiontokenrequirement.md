---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: ade55a5b26826633faf2e7ef7598a4071d613bbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152544"
---
# \<sessionTokenRequirement>
<span data-ttu-id="bdba5-101">Zapewnia konfigurację <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="bdba5-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="bdba5-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdba5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bdba5-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bdba5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="bdba5-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bdba5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bdba5-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bdba5-105">Attributes</span></span>  
  
|<span data-ttu-id="bdba5-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bdba5-106">Attribute</span></span>|<span data-ttu-id="bdba5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bdba5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bdba5-108">cykl życia</span><span class="sxs-lookup"><span data-stu-id="bdba5-108">lifetime</span></span>|<span data-ttu-id="bdba5-109">Określa okres istnienia tokenów sesji.</span><span class="sxs-lookup"><span data-stu-id="bdba5-109">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bdba5-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bdba5-110">Child Elements</span></span>  
 <span data-ttu-id="bdba5-111">Brak</span><span class="sxs-lookup"><span data-stu-id="bdba5-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bdba5-112">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bdba5-112">Parent Elements</span></span>  
  
|<span data-ttu-id="bdba5-113">Element</span><span class="sxs-lookup"><span data-stu-id="bdba5-113">Element</span></span>|<span data-ttu-id="bdba5-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bdba5-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="bdba5-115">Dodaje określony program obsługi tokenów zabezpieczających do kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="bdba5-115">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bdba5-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="bdba5-116">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
