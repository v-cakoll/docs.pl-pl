---
title: ICorDebugExceptionObjectCallStackEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
ms.openlocfilehash: 6c742f541b358b40e6e2fd44ca437b0dd72e29b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091083"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>ICorDebugExceptionObjectCallStackEnum::Next — Metoda
Pobiera określoną liczbę wystąpień [CorDebugExceptionObjectStackFrame —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) , które zawierają informacje z stosu wywołań obiektu wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba wystąpień [CorDebugExceptionObjectStackFrame —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) do pobrania.  
  
 `values`  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt [CorDebugExceptionObjectStackFrame —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) .  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby zwróconych wystąpień [CorDebugExceptionObjectStackFrame —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) .  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugExceptionObjectCallStackEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
