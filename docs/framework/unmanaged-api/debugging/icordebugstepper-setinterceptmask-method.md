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
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791769"
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
  
 Metoda `SetInterceptMask` może mieć nieprzewidziane interakcje z [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika). Na przykład, jeśli jedyną widoczną częścią (czyli niewewnętrzną) fragmentu kodu inicjującego nie są informacje mapowania, a STOP_NO_MAPPING_INFO nie jest ustawiona (patrz metoda [ICorDebugStepper:: SetUnmappedStopMask —](icordebugstepper-setunmappedstopmask-method.md) i Wyliczenie CorDebugUnmappedStop —), stepper będzie przekroczyć inicjalizację klasy. Domyślnie zostanie użyta tylko INTERCEPT_NONE wartość wyliczenia `CorDebugIntercept`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
