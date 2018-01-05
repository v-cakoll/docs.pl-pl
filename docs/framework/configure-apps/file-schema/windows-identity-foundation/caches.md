---
title: "&lt;pamięci podręczne&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b9dfa7b2f0952f3f9e224ad51fd4d9c0c263ce04
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcachesgt"></a>&lt;pamięci podręczne&gt;
Rejestruje pamięci podręczne tokeny sesji i wykrywania powtórzeń tokenów.  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<buforuje >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|Rejestruje pamięci podręcznej sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.|  
|[\<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|Rejestruje pamięci podręcznej powtórzeń tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości poziomu usług.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Zapewnia token obsługi konfiguracji dla kolekcji zabezpieczeń.|  
  
## <a name="remarks"></a>Uwagi  
 A `<caches>` elementu można określić na poziomie usługi pod `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w obszarze `<securityTokenHandlerConfiguration>` elementu. Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.  
  
 `<caches>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> klasy. Skonfigurowany pamięci podręcznych są reprezentowane przez <xref:System.IdentityModel.Configuration.IdentityModelCaches> klasy.  
  
## <a name="example"></a>Przykład  
 Następujący kod XML przedstawia konfigurację pamięci podręcznej niestandardowy do przechowywania sesji tokenów zabezpieczających (<xref:System.IdentityModel.Tokens.SessionSecurityToken>). Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki.  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
