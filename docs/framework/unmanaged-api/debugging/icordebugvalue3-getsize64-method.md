---
title: ICorDebugValue3::GetSize64 — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c0b45e08f7b88d9374023f95c6e3e22139c8949
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144771"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 — Metoda
Pobiera rozmiar w bajtach to [icordebugvalue3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pSize  
 [out] Wskaźnik do rozmiaru, w bajtach, tego obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ta wartość typ jest typem referencyjnym, ta metoda zwraca rozmiar wskaźnika, a nie rozmiar obiektu.  
  
 `ICorDebugValue3::GetSize` Metoda różni się od [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) metoda w typie jako parametr wyjściowy. W [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md), parametr wyjściowy jest `ULONG32`; w `ICorDebugValue3::GetSize`, jest `ULONG64`. Dzięki temu [icordebugvalue3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) interfejsu, aby zgłosić rozmiar tablic, które przekracza 2 GB.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
