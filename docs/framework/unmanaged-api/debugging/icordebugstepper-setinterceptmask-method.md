---
title: ICorDebugStepper::SetInterceptMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: aaba751a58e5b23b98b1d0629ea3cc9e1e7a83a9
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379006"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask — Metoda
Ustawia wartość określającą typy kodu, do którego nastąpi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 podczas Kombinacja wartości wyliczenia CorDebugIntercept —, która określa typy kodu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ustawiono bit dla interceptora, stepper zakończy się po napotkaniu danego typu kodu przechwycenia. Jeśli bit jest wyczyszczony, kod przechwycenia zostanie pominięty.  
  
 `SetInterceptMask`Metoda może mieć nieprzewidziane interakcje z [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika). Na przykład, jeśli jedyną widoczną częścią (czyli niewewnętrzną) fragmentu kodu inicjującego nie są informacje mapowania, a STOP_NO_MAPPING_INFO nie jest ustawiona (patrz metoda [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) i Wyliczenie CorDebugUnmappedStop —), stepper będzie przekroczyć inicjalizację klasy. Domyślnie `CorDebugIntercept` zostanie użyta tylko INTERCEPT_NONE wartość wyliczenia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
