---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e666bac0be772e417f140e1482649f82ea70e2f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673423"
---
# <a name="callbacktimeouts"></a>\<callbackTimeouts>
Określa wartość limitu czasu podczas przepływu transakcji z serwera do klienta.w scenariuszu kontraktu dwustronnego wywołania zwrotnego.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<callbackTimeOuts>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`transactionTimeout`|A <xref:System.TimeSpan> wartość, która określa przedział czasu, w ramach którego transakcje muszą się ukończyć lub automatycznie zakończone. Wartość domyślna to "00: 00:00".|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
