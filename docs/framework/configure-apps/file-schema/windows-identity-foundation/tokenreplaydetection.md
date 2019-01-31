---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 4deeb1d84f2621adb7ff1b649a505138b6856ec1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283078"
---
# <a name="tokenreplaydetection"></a>\<tokenReplayDetection>
Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<tokenReplayDetection>  
  
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
|Włączone|Wartość, która określa, czy jest włączone wykrywanie powtórzeń tokenów; "true", aby umożliwić token wykrywania powtarzania.|  
|expirationPeriod|Element <xref:System.TimeSpan> , który określa maksymalną ilość czasu, zanim element zostanie uznane za wygasłe i usuwane z pamięci podręcznej.  Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Określa ustawienia tożsamości na poziomie usługi.|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Udostępnia konfigurację dla kolekcji zabezpieczeń programy obsługi tokenów.|  
  
## <a name="remarks"></a>Uwagi  
 A `<tokenReplayDetection>` element może być określony na poziomie usługi w ramach `<identityConfiguration>` element lub na poziomie kolekcji programu obsługi tokenów zabezpieczeń w ramach `<securityTokenHandlerConfiguration>` elementu. Ustawienia w kolekcji programu obsługi tokenów zastępują ustawienia określone w usłudze.  
  
 Typ pamięci podręcznej powtórzeń tokenów jest określany przez [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elementu.
