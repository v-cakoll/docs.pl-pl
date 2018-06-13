---
title: ICorDebugProcess::ClearCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2515e21ec00bd656eafd21a092a27304f7b1769
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419019"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException — Metoda
Czyści niezarządzane bieżącego wyjątku dla danego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku wyczyszczone bieżący wyjątek niezarządzane.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) po zgłosił niezarządzany wyjątek, który powinien być ignorowane przez obiekt debugowany wątek. Spowoduje to wyczyszczenie zarówno oczekujących wewnątrzpasmowe (IB), jak i poza pasmem (OOB) zdarzenia dla danego wątku. Wszystkie punkty przerwania OOB i pojedynczy krok wyjątki zostaną automatycznie wyczyszczone.  
  
 Użyj [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) przechwycenia bieżącego zarządzany wyjątek w wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
