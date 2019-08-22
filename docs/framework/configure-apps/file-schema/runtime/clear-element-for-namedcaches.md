---
title: <clear>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658862"
---
# <a name="clear-element-for-namedcaches"></a>\<clear> Element for \<namedCaches>
Czyści wszystkie `namedCache` wpisy `namedCaches` w kolekcji pamięci podręcznej pamięci.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches>  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
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
 Element czyści wszystkie `namedCache` wpisy w kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej. `clear` Można użyć `clear` elementu przed użyciem elementu, `add` aby dodać nowy nazwany wpis pamięci podręcznej w celu uzyskania pewności, że w kolekcji nie ma innych nazwanych pamięci podręcznych.  
  
## <a name="see-also"></a>Zobacz także

- [\<namedCaches >, element (ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
