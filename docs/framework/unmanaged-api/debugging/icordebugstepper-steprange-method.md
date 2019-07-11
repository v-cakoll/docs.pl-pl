---
title: ICorDebugStepper::StepRange — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760536"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange — Metoda
Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku i wrócić po osiągnięciu kodu poza ostatnią z określonymi zakresami.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Ustaw `true` aby wejść do funkcji, która jest wywołana w wątku. Ustaw `false` do kroku za pośrednictwem funkcji.  
  
 `ranges`  
 [in] Tablica cor_debug_step_range — struktur, z których każdy określa zakres.  
  
 `cRangeCount`  
 [in] Rozmiar `ranges` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `StepRange` Metoda działa jak [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, z tą różnicą, że nie zostanie zakończone aż do kodu, zakres zostanie osiągnięty.  
  
 Może to być bardziej efektywne niż przechodzenie krok po kroku jednej instrukcji w danym momencie. Zakresy są określane jako lista par przesunięcia od początku stepper ramki.  
  
 Zakresy są względne wobec kod Microsoft intermediate language (MSIL) metody. Wywołaj [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false` się zakresy względem kodu natywnego metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
