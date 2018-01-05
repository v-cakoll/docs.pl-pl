---
title: '&lt;callbackDebug&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4073feda-1857-4be4-9947-227afb847ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccb48efcdd1924ade27220a685e146a7f5eeef76
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltcallbackdebuggt"></a>&lt;callbackDebug&gt;
Określa usługę debugowania dla [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] obiektu wywołania zwrotnego.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<endpointBehaviors >  
\<zachowanie >  
\<callbackDebug >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<callbackDebug  includeExceptionDetailInFaults="Boolean" />  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`includeExceptionDetailInFaults`|Wartość, która określa, czy obiekty klienta wywołania zwrotnego wrócić informacje o zarządzanym wyjątku w błędach SOAP do usługi.<br /><br /> Jeśli ustawisz ten atrybut `true` programowo, można włączyć przepływ informacji o zarządzanych wyjątku w obiekcie klienta wywołania zwrotnego do usługi w celu debugowania. **Uwaga:** zwraca informacje o zarządzanym wyjątku do klientów mogą stanowić zagrożenie bezpieczeństwa. Jest to spowodowane szczegóły wyjątku ujawnienie informacji o implementacji usługi wewnętrznego, które mogą być używane przez nieautoryzowanych klientów.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.CallbackDebugElement>  
 <xref:System.ServiceModel.Description.CallbackDebugBehavior>
