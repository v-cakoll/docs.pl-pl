---
title: '&lt;diagnostics&gt; w Activation'
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 4e5332eed87ded51cebcd614f45cbc8e80e570fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiagnosticsgt-for-activation"></a>&lt;diagnostics&gt; w Activation
Konfiguruje funkcje diagnostyki odbiornika usługi Windows Communication Foundation (WCF).  
  
 \<system.serviceModel.activation>  
\<Diagnostyka >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`performanceCountersEnabled`|Wartość logiczna wskazująca, czy liczniki wydajności są włączone w celach diagnostycznych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
