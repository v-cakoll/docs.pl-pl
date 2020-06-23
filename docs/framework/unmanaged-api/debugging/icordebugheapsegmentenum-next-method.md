---
title: ICorDebugHeapSegmentEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904276"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next — Metoda
Pobiera określoną liczbę wystąpień [COR_SEGMENT](cor-segment-structure.md) zawierających informacje o regionach pamięci zarządzanej sterty.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 podczas Liczba segmentów, które mają zostać pobrane.  
  
 segmenty  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_SEGMENT](cor-segment-structure.md) , który zawiera informacje o regionie pamięci w zarządzanym stosie.  
  
 pceltFetched  
 określoną Wskaźnik do liczby obiektów [COR_SEGMENT](cor-segment-structure.md) faktycznie zwróconych w `segments` . Ta wartość może być równa `null` `celt` 1.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugHeapSegmentEnum — Interfejs](icordebugheapsegmentenum-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
