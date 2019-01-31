---
title: <remove> — Element do <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 22d06ab1df0d5ed74073772302421a680f1665ef
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257022"
---
# <a name="remove-element-for-namedcaches"></a>\<remove> Element for \<namedCaches>
Usuwa wpis nazwaną pamięć podręczną z `namedCaches` kolekcji w pamięci podręcznej.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<remove>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `None`  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 `None`  
  
### <a name="child-elements"></a>Elementy podrzędne  
 `None`  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Usuwa element `namedCache` wpis z kolekcji nazwaną pamięć podręczną dla pamięci podręcznej.  
  
## <a name="see-also"></a>Zobacz także
- [\<namedCaches >, Element (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
