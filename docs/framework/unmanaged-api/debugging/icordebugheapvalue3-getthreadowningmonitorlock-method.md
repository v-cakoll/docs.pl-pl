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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1678f1de7c23387f028348dadbc7b61e2cdc035c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201432"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda
Zwraca wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThread`  
 [out] Wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.  
  
 `pAcquisitionCount`  
 [out] Ile razy ten wątek musi zwolnić blokadę przed zwróceniem jest bez właściciela.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|S_FALSE|Nie wątków zarządzanych jest właścicielem blokady monitora dla tego obiektu.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wątek jest właścicielem blokady monitora dla tego obiektu:  
  
-   Metoda zwraca wartość S_OK.  
  
-   Obiekt wątku jest prawidłowy, aż wątek kończy działanie.  
  
 Jeśli nie wątków zarządzanych jest właścicielem blokady monitora dla tego obiektu `ppThread` i `pAcquisitionCount` ulegną zmianie, a metoda zwraca wartość S_FALSE.  
  
 Jeśli `ppThread` lub `pAcquisitionCount` nie jest prawidłową wskaźnikiem, wynik jest niezdefiniowany.  
  
 W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, który, wątek jest właścicielem blokady monitora dla tego obiektu, metoda zwraca wartość HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
