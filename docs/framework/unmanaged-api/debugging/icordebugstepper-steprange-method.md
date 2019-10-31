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
ms.openlocfilehash: 2ca4542fe42fab0b5ff54b23b9492d3906698c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120620"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange — Metoda
Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku i zwraca, gdy osiągnie kod poza ostatnim z określonych zakresów.  
  
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
 podczas Ustaw, aby `true` wkroczyć do funkcji, która jest wywoływana w wątku. Ustaw na `false`, aby przekroczyć funkcję.  
  
 `ranges`  
 podczas Tablica struktur COR_DEBUG_STEP_RANGE, z których każdy określa zakres.  
  
 `cRangeCount`  
 podczas Rozmiar tablicy `ranges`.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `StepRange` działa jak Metoda [ICorDebugStepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) , z tą różnicą, że nie zostanie ukończona, dopóki nie zostanie osiągnięty kod poza podanym zakresem.  
  
 Może to być wydajniejsze niż wykonywanie jednej instrukcji w danym momencie. Zakresy są określone jako lista par przesunięcia od początku ramki stepper.  
  
 Zakresy są względne dla kodu języka pośredniego firmy Microsoft (MSIL) metody. Wywołaj [ICorDebugStepper:: SetRangeIL —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false`, aby uczynić zakresy względem kodu natywnego metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
