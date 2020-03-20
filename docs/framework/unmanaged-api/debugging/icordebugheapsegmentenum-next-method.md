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
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178897"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next — Metoda
Pobiera określoną liczbę [COR_HEAPOBJECT](cor-heapobject-structure.md) wystąpień, które zawierają informacje o regionach pamięci zarządzanego stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 Celt  
 [w] Liczba segmentów do pobrania.  
  
 segmenty  
 [na zewnątrz] Tablica wskaźników, z których każdy wskazuje [na obiekt COR_HEAPOBJECT,](cor-heapobject-structure.md) który zawiera informacje o regionie pamięci w zarządzanym stosie.  
  
 pceltFetched  
 [na zewnątrz] Wskaźnik do liczby [obiektów COR_HEAPOBJECT](cor-heapobject-structure.md) faktycznie zwróconych `segments`w . Ta wartość `null` może `celt` być, jeśli jest 1.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugHeapSegmentEnum, interfejs](icordebugheapsegmentenum-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
