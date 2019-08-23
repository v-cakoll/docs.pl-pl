---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943710"
---
# <a name="sessionsecuritytokencache"></a>\<sessionSecurityTokenCache>
Rejestruje pamięć podręczną tokenów sesji za pomocą usługi lub kolekcji obsługi tokenów zabezpieczających.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<pamięć podręczna >  
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
|— typ|Typ, który pochodzi od <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> klasy.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<pamięć podręczna >](caches.md)|Rejestruje pamięci podręczne używane przez usługę lub kolekcję programu obsługi tokenów zabezpieczających.|  
  
## <a name="example"></a>Przykład  
 W poniższym kodzie XML przedstawiono konfigurację niestandardowej pamięci podręcznej dla tokenów zabezpieczających<xref:System.IdentityModel.Tokens.SessionSecurityToken>sesji (). Konfiguracja jest pobierana z `ClaimsAwareWebFarm` przykładu. Aby uzyskać więcej informacji na temat tego przykładu, zobacz [indeks przykładowego kodu WIF](../../../security/wif-code-sample-index.md).  
  
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
