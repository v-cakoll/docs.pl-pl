---
title: "&lt;Wyczyść&gt; elementu &lt;namedCaches&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0819141b2135a2de99a2801a1888f7b0e1cd19fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a>&lt;Wyczyść&gt; elementu &lt;namedCaches&gt;
Czyści wszystkie `namedCache` wpisów w `namedCaches` kolekcji dla pamięci podręcznej.  
  
 \<System.Runtime.Caching — >  
\<memoryCache >  
\<namedCaches >  
\<Dodaj >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<namedCaches>  
    <clear name="default" />  
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
|[\<namedCaches >](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Zawiera kolekcję ustawień konfiguracyjnych dla nazwanego <xref:System.Runtime.Caching.MemoryCache> wystąpień.|  
  
## <a name="remarks"></a>Uwagi  
 `clear` Element czyści wszystkie `namedCache` wpisów w kolekcji nazwanych pamięci podręcznej w pamięci podręcznej. Można użyć `clear` element przed użyciem `add` element, aby dodać nowy wpis pamięci podręcznej o nazwie, aby mieć pewność, nie ma żadnych innych o nazwie pamięci podręcznych w kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [\<namedCaches > elementu (ustawienia pamięci podręcznej)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
