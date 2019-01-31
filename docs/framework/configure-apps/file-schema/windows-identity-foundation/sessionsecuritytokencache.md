---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 697c20d1f526cb376c2430f0006349f7d8f9b2f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257945"
---
# <a name="sessionsecuritytokencache"></a>\<sessionSecurityTokenCache>
Rejestruje pamięci podręcznej dla sesji tokenów z usługi lub kolekcji programu obsługi tokenów zabezpieczeń.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<caches>  
\<sessionSecurityTokenCache>  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|— typ|Typ, który pochodzi od klasy <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<caches>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Rejestruje pamięci podręcznych, używane przez usługę lub kolekcji programu obsługi tokenów zabezpieczeń.|  
  
## <a name="example"></a>Przykład  
 Następujący kody XML pokazuje konfiguracji niestandardowej pamięci podręcznej do przechowywania tokenów zabezpieczających sesji (<xref:System.IdentityModel.Tokens.SessionSecurityToken>). Konfiguracja jest pobierana z `ClaimsAwareWebFarm` próbki. Aby uzyskać więcej informacji na temat tego przykładu, zobacz [Indeks przykładów kodu programu WIF](../../../../../docs/framework/security/wif-code-sample-index.md).  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>
