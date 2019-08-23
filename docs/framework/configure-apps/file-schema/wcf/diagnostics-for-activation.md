---
title: <diagnostics>na potrzeby aktywacji
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: 543c41936921eda39017e07f1c97294b268a9141
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919218"
---
# <a name="diagnostics-for-activation"></a>\<> diagnostyki na potrzeby aktywacji
Konfiguruje funkcje diagnostyki odbiornika Windows Communication Foundation (WCF).  
  
 \<system.serviceModel.activation>  
\<> diagnostyki  
  
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
|`performanceCountersEnabled`|Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
