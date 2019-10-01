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
ms.openlocfilehash: bdf59ee3c7bf41a2bb0ff68db5e70dd5a519a0e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700780"
---
# <a name="icordebugcontrollercontinue-method"></a>ICorDebugController::Continue — Metoda

Wznawia wykonywanie zarządzanych wątków po wywołaniu [metody Stop](icordebugcontroller-stop-method.md).

## <a name="syntax"></a>Składnia

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a>Parametry

 `fIsOutOfBand`  
 podczas Ustaw wartość `true` w przypadku kontynuowania z poziomu zdarzenia poza pasmem. w przeciwnym razie ustaw wartość `false`.

## <a name="remarks"></a>Uwagi

`Continue` kontynuuje proces po wywołaniu metody `ICorDebugController::Stop`.

Podczas przeprowadzania debugowania w trybie mieszanym nie należy wywoływać `Continue` w wątku zdarzenia Win32, chyba że będziesz kontynuować z poziomu zdarzenia poza pasmem.

*Zdarzenie w paśmie* jest zdarzeniem zarządzanym lub normalnym niezarządzanym zdarzeniem, w którym debuger obsługuje interakcje ze stanem zarządzanym procesu. W takim przypadku debuger otrzymuje wywołanie zwrotne [ICorDebugUnmanagedCallback::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) z parametrem `fOutOfBand` ustawionym na `false`.
  
*Zdarzenie poza pasmem* jest zdarzeniem niezarządzanym, podczas którego interakcja ze stanem zarządzanym procesu jest niemożliwa, gdy proces został zatrzymany z powodu zdarzenia. W takim przypadku debuger otrzymuje wywołanie zwrotne `ICorDebugUnmanagedCallback::DebugEvent` z parametrem `fOutOfBand` ustawionym na `true`.

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Nagłówek:** CorDebug. idl, CorDebug. h

 **Biblioteka:** CorGuids. lib

 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
 
