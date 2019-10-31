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
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137585"
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
  
 Metoda `SetInterceptMask` może mieć nieprzewidziane interakcje z [ICorDebugStepper:: SetUnmappedStopMask —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika). Na przykład, jeśli jedyną widoczną częścią (czyli niewewnętrzną) fragmentu kodu inicjującego nie są informacje o mapowaniu i STOP_NO_MAPPING_INFO nie jest ustawiony (zobacz [ICorDebugStepper:: SetUnmappedStopMask —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) i CorDebugUnmappedStop — Wyliczenie) stepper będzie przekroczyć inicjalizację klasy. Domyślnie zostanie użyta tylko wartość INTERCEPT_NONE wyliczenia `CorDebugIntercept`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
