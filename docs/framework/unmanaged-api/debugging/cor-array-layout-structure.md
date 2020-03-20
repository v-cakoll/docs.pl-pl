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
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179351"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT — Struktury
Zawiera informacje o układzie obiektu tablicowego w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`componentID`|Identyfikator typu obiektów, które zawiera tablica.|  
|`componentType`|A CorElementType wartość wyliczenia, która wskazuje, czy składnik jest odwołanie do wyrzucania elementów bezużytecznych, klasy wartości lub pierwotne.|  
|`firstElementOffset`|Przesunięcie do pierwszego elementu w tablicy.|  
|`elementSize`|Rozmiar każdego elementu.|  
|`countOffset`|Przesunięcie do liczby elementów w tablicy.|  
|`rankSize`|Rozmiar rangi w bajtach.|  
|`numRanks`|Liczba szeregów w tablicy.|  
|`rankOffset`|Przesunięcie, od którego zaczynają się rangi.|  
  
## <a name="remarks"></a>Uwagi  
 Pole `rankSize` określa rozmiar rangi w tablicy wielowymiarowej. Jest to dokładne dla tablic jednowymiarowych, jak również.  
  
 Wartość `numRanks` wynosi 1 dla tablicy jednowymiarowej i `N` wielowymiarowej tablicy wymiarów. `N`  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugging](index.md)
