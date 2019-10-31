---
title: ICorDebugThread4::GetBlockingObjects — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: e4d5582b7a3df16db58ea0ed001dcbffcdcaab79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122460"
---
# <a name="icordebugthread4getblockingobjects-method"></a>ICorDebugThread4::GetBlockingObjects — Metoda
Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a>Parametry  
 `ppBlockingObjectEnum`  
 określoną Wskaźnik do uporządkowanego wyliczania struktur [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy element w zwracanym wyliczeniu odpowiada pierwszej strukturze, która blokuje wątek. Drugi element odnosi się do bloku elementu, który jest napotkany podczas wykonywania wywołania procedury asynchronicznej (APC), gdy jest zablokowany w pierwszej i tak dalej.  
  
 Wyliczenie jest prawidłowe tylko dla czasu trwania bieżącego zsynchronizowanego stanu.  
  
 Ta metoda musi być wywoływana, gdy debugowanego obiektu jest w stanie zsynchronizowanym.  
  
 Jeśli `ppBlockingObjectEnum` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.  
  
 Jeśli wątek jest zablokowany i nie można ustalić błędu, metoda zwraca wartość HRESULT, która wskazuje na błąd; w przeciwnym razie zwraca S_OK.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
