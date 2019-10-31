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
ms.openlocfilehash: f37bf545553045b9737b7057feed78e1f06ace4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099469"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT — Struktury
Zawiera informacje o układzie obiektu tablicy w pamięci.  
  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`componentID`|Identyfikator typu obiektów, które zawiera tablica.|  
|`componentType`|Wartość wyliczenia CorElementType —, która wskazuje, czy składnik jest odwołaniem do wyrzucania elementów bezużytecznych, klasą wartości lub elementem pierwotnym.|  
|`firstElementOffset`|Przesunięcie do pierwszego elementu w tablicy.|  
|`elementSize`|Rozmiar każdego elementu.|  
|`countOffset`|Przesunięcie do liczby elementów w tablicy.|  
|`rankSize`|Rozmiar rangi w bajtach.|  
|`numRanks`|Liczba rangi w tablicy.|  
|`rankOffset`|Przesunięcie, od którego są uruchamiane Range.|  
  
## <a name="remarks"></a>Uwagi  
 Pole `rankSize` określa rozmiar rangi w tablicy wielowymiarowej. Jest to dokładne dla tablic jednowymiarowych.  
  
 Wartość `numRanks` to 1 dla jednowymiarowej tablicy i `N` dla wielowymiarowej tablicy wymiarów `N`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
