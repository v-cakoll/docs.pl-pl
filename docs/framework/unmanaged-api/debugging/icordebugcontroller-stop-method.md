---
title: ICorDebugController::Stop — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db8c5c8dbb5bf3ff8bc7202a60397180b7b38
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749069"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop — Metoda
Wykonuje wspólne stop we wszystkich wątkach, na których uruchomiono kod zarządzany w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwTimeoutIgnored`  
 Nie używany.  
  
## <a name="remarks"></a>Uwagi  
 `Stop` wykonuje kod zatrzymania współpracy na wszystkie wątki uruchomione zarządzanych w procesie. Podczas sesji debugowania tylko do zarządzanych niezarządzanych wątków może kontynuować działanie (ale będą blokowane podczas próby wywołania kodu zarządzanego). Podczas debugowania międzyoperacyjnego sesji również zostaną zatrzymane niezarządzanych wątków. `dwTimeoutIgnored` Wartość aktualnie jest ignorowany i traktowany jako NIESKOŃCZONE (-1). Jeśli współpracy stop zakończy się niepowodzeniem z powodu zakleszczenia, wszystkie wątki są wstrzymywane i E_TIMEOUT jest zwracana.  
  
> [!NOTE]
>  `Stop` jest tylko synchroniczne metody w interfejsie API debugowania. Gdy `Stop` zwraca wartość S_OK, proces został zatrzymany. Nie wywołania zwrotnego otrzymuje o ogranicznika. Debuger musi wywołać [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) umożliwia wznowienie procesu.  
  
 Debuger obsługuje licznika zatrzymania. Gdy licznik zbliża się do zera, jest wznawiany kontrolera. Każde wywołanie `Stop` lub każdego wysłane wywołanie zwrotne zwiększa wartość licznika. Każde wywołanie `ICorDebugController::Continue` zmniejsza wartość licznika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
