---
title: ICorDebugProcess5::GetGCHeapInformation — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 3aa9fe884b16a239f5105dd262edeb8fc3e4abaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084403"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation — Metoda
Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy jest obecnie wyliczalne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pHeapInfo`  
 określoną Wskaźnik do wartości [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , która zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 Metodę `ICorDebugProcess5::GetGCHeapInformation` należy wywołać przed wyliczeniem sterty lub poszczególnych regionów sterty, aby upewnić się, że struktury wyrzucania elementów bezużytecznych w procesie są obecnie prawidłowe. Nie można przeprowadzić sterty odzyskiwania pamięci, gdy kolekcja jest w toku. W przeciwnym razie Wyliczenie może przechwytywać nieprawidłowe struktury wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
