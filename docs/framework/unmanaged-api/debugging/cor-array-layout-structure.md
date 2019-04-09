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
ms.openlocfilehash: a3a5a5bb26912c87cdf37ba0d8f0cee1cf1ffa97
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142015"
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT — Struktury
Informacje dotyczące układu obiektu tablicowego w pamięci.  
  
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
|`componentType`|Corelementtype — wartość wyliczenia, która wskazuje, czy składnik jest odwołanie do kolekcji wyrzucania elementów, klasą wartości lub elementu podstawowego.|  
|`firstElementOffset`|Przesunięcie do pierwszego elementu w tablicy.|  
|`elementSize`|Rozmiar każdego elementu.|  
|`countOffset`|Przesunięcie do liczby elementów w tablicy.|  
|`rankSize`|Rozmiar w bajtach rangi.|  
|`numRanks`|Liczba rangę tablicy.|  
|`rankOffset`|Przesunięcie, w którym start rangę.|  
  
## <a name="remarks"></a>Uwagi  
 `rankSize` Pola określa rozmiar rangę tablicy wielowymiarowej. Jest prawidłowe dla także tablice jednowymiarowe.  
  
 Wartość `numRanks` 1 dla tablicy jednowymiarowej i `N` dla tablicy wielowymiarowej `N` wymiarów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
