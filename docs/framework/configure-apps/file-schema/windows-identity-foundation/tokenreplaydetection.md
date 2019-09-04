---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251768"
---
# <a name="tokenreplaydetection"></a>\<tokenReplayDetection>
Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayDetection >**  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a>Typ  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|dostępny|Wartość określająca, czy jest włączone wykrywanie powtarzania tokenów; wartość "true" w celu włączenia wykrywania powtarzania tokenu.|  
|expirationPeriod|A <xref:System.TimeSpan> , która określa maksymalny czas, po upływie którego element zostanie uznany za wygasły i usunięty z pamięci podręcznej.  Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usług.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Zapewnia konfigurację kolekcji programów obsługi tokenów zabezpieczających.|  
  
## <a name="remarks"></a>Uwagi  
 Element można określić na poziomie usługi `<identityConfiguration>` pod elementem lub na poziomie kolekcji `<securityTokenHandlerConfiguration>` programu obsługi tokenów zabezpieczających w ramach elementu. `<tokenReplayDetection>` Ustawienia w kolekcji obsługi tokenów zastępują te określone w usłudze.  
  
 Typ pamięci podręcznej powtarzania tokenów jest określany przez [ \<element > tokenReplayCache](tokenreplaycache.md) .
