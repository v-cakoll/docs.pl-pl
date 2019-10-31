---
title: ICorDebugHeapEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 1beb69bfaad9acb9c269ad8becb81bea64edb6a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138468"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next — Metoda
Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 podczas Liczba obiektów do pobrania.  
  
 — obiekty  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , który zawiera informacje o obiekcie na zarządzanym stosie.  
  
 pceltFetched  
 określoną Wskaźnik do liczby obiektów [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) faktycznie zwróconych w `objects`. Ta wartość może być `null`, jeśli `celt` wynosi 1.  
  
## <a name="remarks"></a>Uwagi  
 Pole `COR_HEAPOBJECT.type` jest identyfikatorem zagnieżdżonego, odwołującego się interfejsu COM. To odwołanie musi zostać wydane przez obiekt wywołujący `ICorDebugHeapEnum::Next`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugHeapEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
