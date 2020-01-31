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
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791706"
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
 Metoda `StepRange` działa jak Metoda [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , z tą różnicą, że nie zostanie ukończona, dopóki nie zostanie osiągnięty kod poza podanym zakresem.  
  
 Może to być wydajniejsze niż wykonywanie jednej instrukcji w danym momencie. Zakresy są określone jako lista par przesunięcia od początku ramki stepper.  
  
 Zakresy są względne dla kodu języka pośredniego firmy Microsoft (MSIL) metody. Wywołaj [ICorDebugStepper:: SetRangeIL —](icordebugstepper-setrangeil-method.md) z `false`, aby uczynić zakresy względem kodu natywnego metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
