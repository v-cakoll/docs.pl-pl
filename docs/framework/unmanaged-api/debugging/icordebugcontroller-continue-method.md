---
title: ICorDebugController::Continue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7eacffe5769bc77ab626f6adbc99db1137da565f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146812"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue — Metoda
Wznawia wykonywanie wątków zarządzanych po wywołaniu [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fIsOutOfBand`  
 [in] Ustaw `true` Jeśli kontynuując zdarzenie out-of-band; w przeciwnym razie wartość `false`.  
  
## <a name="remarks"></a>Uwagi  
 `Continue` kontynuuje proces po wywołaniu `ICorDebugController::Stop` metody.  
  
 Podczas ustalania, debugowanie w trybie mieszanym, nie należy wywoływać metody `Continue` na Win32 zdarzeń wątku, chyba że trwają ze zdarzenia poza pasmem.  
  
 *Zdarzeń wewnątrzpasmowe* jest zdarzenie zarządzane lub normalne zdarzeń niezarządzanych, podczas którego debuger obsługuje interakcję z zarządzanego stan procesu. W tym przypadku odbiera jest debugera [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) wywołania zwrotnego z jego `fOutOfBand` parametr `false`.  
  
 *Zdarzeń out-of-band* to zdarzenie niezarządzany, podczas którego interakcji z zarządzanego stan procesu jest niemożliwe, gdy proces zostanie zatrzymany z powodu zdarzenia. W tym przypadku odbiera jest debugera `ICorDebugUnmanagedCallback::DebugEvent` wywołania zwrotnego z jego `fOutOfBand` parametr `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
