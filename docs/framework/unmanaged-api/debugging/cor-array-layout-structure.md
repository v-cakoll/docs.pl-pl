---
title: COR_ARRAY_LAYOUT — Struktury
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a96542ab5113311bba79cc552afd7f29e6eafa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406399"
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT — Struktury
Zawiera informacje o układzie tablicy obiektów w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;   
    ULONG32 rankSize;   
    ULONG32 numRanks;   
    ULONG32 rankOffset;   
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`componentID`|Identyfikator typu obiektów zawartych w tablicy.|  
|`componentType`|Wartość wyliczenia CorElementType, która wskazuje, czy składnik jest odwołanie do kolekcji odzyskiwanie, klasą wartości lub typu pierwotnego.|  
|`firstElementOffset`|Przesunięcie do pierwszego elementu w tablicy.|  
|`elementSize`|Rozmiar każdego elementu.|  
|`countOffset`|Przesunięcie do liczby elementów w tablicy.|  
|`rankSize`|Rozmiar w bajtach stopnia.|  
|`numRanks`|Liczba rangi tablicy.|  
|`rankOffset`|Przesunięcie, jaką start rangę.|  
  
## <a name="remarks"></a>Uwagi  
 `rankSize` Pole określa rozmiar pozycji w tablicy wielowymiarowej. Jest dokładne dla również tablice jednowymiarowe.  
  
 Wartość `numRanks` 1 dla tablicy jednowymiarowej i `N` dla tablicy wielowymiarowej z `N` wymiarów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
