---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646065"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="8c2aa-101">\<> sessionSecurityTokenCache</span><span class="sxs-lookup"><span data-stu-id="8c2aa-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="8c2aa-102">Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="8c2aa-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8c2aa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8c2aa-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="8c2aa-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="8c2aa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="8c2aa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="8c2aa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>pamięci podręcznej**](caches.md)</span><span class="sxs-lookup"><span data-stu-id="8c2aa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="8c2aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sessionSecurityTokenCache**</span><span class="sxs-lookup"><span data-stu-id="8c2aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c2aa-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c2aa-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c2aa-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8c2aa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8c2aa-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c2aa-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8c2aa-111">Attributes</span></span>  
  
|<span data-ttu-id="8c2aa-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8c2aa-112">Attribute</span></span>|<span data-ttu-id="8c2aa-113">Opis</span><span class="sxs-lookup"><span data-stu-id="8c2aa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c2aa-114">type</span><span class="sxs-lookup"><span data-stu-id="8c2aa-114">type</span></span>|<span data-ttu-id="8c2aa-115">Typ, który pochodzi <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> od klasy.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c2aa-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8c2aa-116">Child Elements</span></span>  
 <span data-ttu-id="8c2aa-117">Brak</span><span class="sxs-lookup"><span data-stu-id="8c2aa-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c2aa-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8c2aa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8c2aa-119">Element</span><span class="sxs-lookup"><span data-stu-id="8c2aa-119">Element</span></span>|<span data-ttu-id="8c2aa-120">Opis</span><span class="sxs-lookup"><span data-stu-id="8c2aa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c2aa-121">\<>pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8c2aa-121">\<caches></span></span>](caches.md)|<span data-ttu-id="8c2aa-122">Rejestruje pamięci podręczne używane przez usługę lub kolekcję obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8c2aa-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c2aa-123">Example</span></span>  
 <span data-ttu-id="8c2aa-124">Poniższy kod XML przedstawia konfigurację niestandardowej pamięci<xref:System.IdentityModel.Tokens.SessionSecurityToken>podręcznej do przechowywania tokenów zabezpieczających sesji ( ).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="8c2aa-125">Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.</span><span class="sxs-lookup"><span data-stu-id="8c2aa-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="8c2aa-126">Aby uzyskać więcej informacji na temat tego przykładu, zobacz [Indeks przykładowy kodu WIF](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="8c2aa-126">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8c2aa-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c2aa-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
