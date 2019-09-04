---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252047"
---
# <a name="clear"></a><span data-ttu-id="ade2e-101">\<clear></span><span class="sxs-lookup"><span data-stu-id="ade2e-101">\<clear></span></span>
<span data-ttu-id="ade2e-102">Czyści wszystkie programy obsługi tokenów zabezpieczających z bieżącej kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="ade2e-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
<span data-ttu-id="ade2e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ade2e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ade2e-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="ade2e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="ade2e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="ade2e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="ade2e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="ade2e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="ade2e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="ade2e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ade2e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ade2e-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ade2e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ade2e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ade2e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ade2e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ade2e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ade2e-111">Attributes</span></span>  
 <span data-ttu-id="ade2e-112">Brak</span><span class="sxs-lookup"><span data-stu-id="ade2e-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ade2e-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ade2e-113">Child Elements</span></span>  
 <span data-ttu-id="ade2e-114">Brak</span><span class="sxs-lookup"><span data-stu-id="ade2e-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ade2e-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ade2e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ade2e-116">Element</span><span class="sxs-lookup"><span data-stu-id="ade2e-116">Element</span></span>|<span data-ttu-id="ade2e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ade2e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ade2e-118">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ade2e-118">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="ade2e-119">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="ade2e-119">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
