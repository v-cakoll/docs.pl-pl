---
title: <clear>, element dla <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252757"
---
# <a name="clear-element-for-namedcaches"></a>\<clear>, element dla \<namedCaches>
Czyści wszystkie `namedCache` wpisy w kolekcji pamięci `namedCaches` podręcznej pamięci.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
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
 `clear`Element czyści wszystkie `namedCache` wpisy w kolekcji nazwanych pamięci podręcznej dla pamięci podręcznej. Można użyć `clear` elementu przed użyciem `add` elementu, aby dodać nowy nazwany wpis pamięci podręcznej w celu uzyskania pewności, że w kolekcji nie ma innych nazwanych pamięci podręcznych.  
  
## <a name="see-also"></a>Zobacz także

- [\<namedCaches>— Element (ustawienia pamięci podręcznej)](namedcaches-element-cache-settings.md)
