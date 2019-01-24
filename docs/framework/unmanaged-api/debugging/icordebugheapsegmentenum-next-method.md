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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d0c43b1992d04a89fc21944648b648a127581ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637810"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next — Metoda
Pobiera określoną liczbę [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje dotyczące obszarów pamięci zarządzanej sterty.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 celt  
 [in] Liczba segmentów, które mają zostać pobrane.  
  
 segmenty  
 [out] Tablica wskaźników, z których każdy wskazuje [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiektu, który dostarcza informacji na temat region pamięci w stosie zarządzanym.  
  
 pceltFetched  
 [out] Wskaźnik do liczby [cor_heapobject —](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) obiekty, które faktycznie są zwracane w `segments`. Ta wartość może być `null` Jeśli `celt` 1.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugHeapSegmentEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
