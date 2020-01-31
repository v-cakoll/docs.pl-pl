---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: 8be7c0e32f6183deb354d8b3936ef55c2520fe9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788622"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda
Zwraca zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThread`  
 określoną Zarządzany wątek, który jest właścicielem blokady monitora dla tego obiektu.  
  
 `pAcquisitionCount`  
 określoną Liczba przypadków, w których ten wątek będzie musiał zwolnić blokadę, zanim powróci do elementu będącego właścicielem.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|S_FALSE|Żaden zarządzany wątek nie jest właścicielem blokady monitora dla tego obiektu.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zarządzany wątek jest właścicielem blokady monitora dla tego obiektu:  
  
- Metoda zwraca S_OK.  
  
- Obiekt wątku jest prawidłowy do momentu zakończenia wątku.  
  
 Jeśli żaden zarządzany wątek nie jest właścicielem blokady monitora dla tego obiektu, `ppThread` i `pAcquisitionCount` są niezmienione, a metoda zwraca S_FALSE.  
  
 Jeśli `ppThread` lub `pAcquisitionCount` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.  
  
 Jeśli wystąpi błąd w taki sposób, że nie można ustalić, który z nich jest właścicielem blokady monitora dla tego obiektu, metoda zwraca wartość HRESULT, która wskazuje na błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
