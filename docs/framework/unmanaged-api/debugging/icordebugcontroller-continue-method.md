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
ms.openlocfilehash: 0fd7dfc1a48e21abbc80692c110bee55beb68e6b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892861"
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
podczas Ustaw na `true` w przypadku kontynuowania z poziomu zdarzenia poza pasmem. w przeciwnym razie ustaw `false`wartość.

## <a name="remarks"></a>Uwagi

`Continue`kontynuuje proces po wywołaniu `ICorDebugController::Stop` metody.

Podczas przeprowadzania debugowania w trybie mieszanym Nie wywołuj `Continue` wątku zdarzeń Win32, chyba że będziesz kontynuować z poziomu zdarzenia poza pasmem.

*Zdarzenie w paśmie* jest zdarzeniem zarządzanym lub normalnym niezarządzanym zdarzeniem, w którym debuger obsługuje interakcje ze stanem zarządzanym procesu. W takim przypadku debuger otrzymuje wywołanie zwrotne [ICorDebugUnmanagedCallback::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) z `fOutOfBand` parametrem ustawionym na `false`.

*Zdarzenie poza pasmem* jest zdarzeniem niezarządzanym, podczas którego interakcja ze stanem zarządzanym procesu jest niemożliwa, gdy proces został zatrzymany z powodu zdarzenia. W takim przypadku debuger odbiera `ICorDebugUnmanagedCallback::DebugEvent` wywołanie zwrotne z `fOutOfBand` parametrem ustawionym na `true`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
