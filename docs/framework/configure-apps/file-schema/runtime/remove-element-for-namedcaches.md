---
title: <remove>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: e9b126cee83bc8109606d915ea48549beea970c9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663476"
---
# <a name="remove-element-for-namedcaches"></a>\<remove> Element for \<namedCaches>
Usuwa wpis nazwanej pamięci podręcznej z `namedCaches` kolekcji dla pamięci podręcznej.  
  
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
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracji dla nazwanych <xref:System.Runtime.Caching.MemoryCache> wystąpień.|  
  
## <a name="remarks"></a>Uwagi  
 `remove` Element`namedCache` usuwa wpis z kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej.  
  
## <a name="see-also"></a>Zobacz także

- [\<namedCaches >, element (ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
