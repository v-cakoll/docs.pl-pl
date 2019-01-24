---
title: '&lt;callbackDebug&gt;'
ms.date: 03/30/2017
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
ms.openlocfilehash: 1aa292a3fe06af9cf1dbc53ebf5bbdf9841be8d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687378"
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Określa usługę debugowania dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).  
  
 \<system.ServiceModel>  
\<zachowania >  
\<endpointBehaviors>  
\<zachowanie >  
\<callbackDebug>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<callbackDebug includeExceptionDetailInFaults="Boolean" />
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|Wartość, która określa, czy obiekty klienta wywołania zwrotnego zwracają informacje o zarządzanym wyjątku w błędach SOAP powrót do usługi.<br /><br /> Jeśli ten atrybut jest ustawiony `true` programowo, można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania. **Uwaga:**  Zwracanie informacje o zarządzanym wyjątku do klientów może stanowić zagrożenie bezpieczeństwa. Jest to spowodowane szczegóły wyjątku ujawniać informacje o implementacji usługi wewnętrznej, która mogłaby być używana przez nieautoryzowane klientów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.ServiceModel.Configuration.CallbackDebugElement>
- <xref:System.ServiceModel.Description.CallbackDebugBehavior>
