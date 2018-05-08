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
ms.openlocfilehash: 838f2df06f8875037edbe39d2db0411f31abe01f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange — Metoda
Powoduje to ICorDebugStepper — aby pojedynczy krok za pomocą jego zawierającego wątku i zwracane w przypadku osiągnie kodu poza ostatniego z określonymi zakresami.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Ustaw `true` do kroku do funkcji, która jest wywoływana w wątku. Ustaw `false` do kroku przez funkcję.  
  
 `ranges`  
 [in] Tablica struktur COR_DEBUG_STEP_RANGE, z których każdy określa zakres.  
  
 `cRangeCount`  
 [in] Rozmiar `ranges` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `StepRange` Metody działa jak [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, z wyjątkiem tego, że nie zostanie ukończone do kodu zakres zostanie osiągnięty.  
  
 Może to być skuteczniejsze niż krokowe wykonywanie jednej instrukcji w czasie. Zakresy są określone jako lista par przesunięcia od początku stepper ramki.  
  
 Zakresy są względem kodu języka pośredniego (MSIL) firmy Microsoft metody. Wywołanie [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false` aby zakresy względem kodu natywnego metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
