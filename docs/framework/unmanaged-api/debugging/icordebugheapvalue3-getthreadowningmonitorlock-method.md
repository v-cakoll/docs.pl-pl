---
title: "ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3571f546f71515a980c5415e568ae85eb0863d42
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a>ICorDebugHeapValue3::GetThreadOwningMonitorLock — Metoda
Zwraca zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThread`  
 [out] Zarządzanego wątku, który jest właścicielem blokady monitora w tym obiekcie.  
  
 `pAcquisitionCount`  
 [out] Ile razy ten wątek musi zwolnić blokady przed zwróceniem do trwa bez właściciela.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|WARTOŚCI S_FALSE|Nie zarządzanego wątku jest właścicielem blokady monitora w tym obiekcie.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zarządzanego wątku jest właścicielem blokady monitora dla tego obiektu:  
  
-   Metoda zwraca wartość S_OK.  
  
-   Obiekt wątku jest prawidłowy, dopóki kończy działanie wątku.  
  
 Jeśli nie zarządzanego wątku jest właścicielem blokady monitora w tym obiekcie `ppThread` i `pAcquisitionCount` nie uległy zmianie, a metoda zwraca wartości S_FALSE.  
  
 Jeśli `ppThread` lub `pAcquisitionCount` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.  
  
 W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, które, wątek jest właścicielem blokady monitora w tym obiekcie metoda zwraca HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
