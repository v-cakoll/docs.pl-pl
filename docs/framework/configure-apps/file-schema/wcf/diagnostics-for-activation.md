---
title: <diagnostics> w celu aktywacji
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: ac235b9a3c125cd3fe63ccd899e2ff92d4d3f31b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278459"
---
# <a name="diagnostics-for-activation"></a>\<Diagnostyka > w celu aktywacji
Umożliwia skonfigurowanie funkcji diagnostyki odbiornika usługi Windows Communication Foundation (WCF).  
  
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
|`performanceCountersEnabled`|Wartość logiczna wskazująca, czy liczniki wydajności są włączone do celów diagnostycznych.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
