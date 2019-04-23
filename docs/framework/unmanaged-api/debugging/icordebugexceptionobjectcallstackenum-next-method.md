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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c33f76b5eaa87c0b69497547732564921f662d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099472"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a>ICorDebugExceptionObjectCallStackEnum::Next — Metoda
Pobiera określoną liczbę [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpień, które zawierają informacje ze stosu wywołań obiekt wyjątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpienia mają zostać pobrane.  
  
 `values`  
 [out] Tablica wskaźników, z których każdy wskazuje [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektu.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpień rzeczywistego zwrotu.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugExceptionObjectCallStackEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
