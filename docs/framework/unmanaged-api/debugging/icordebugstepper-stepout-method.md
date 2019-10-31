---
title: ICorDebugStepper::StepOut — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 6c1d7db8aacaf81d47abd4a9cd972b44f56a3bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137519"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut — Metoda
Powoduje, że ICorDebugStepper to jeden krok za pomocą zawartego w nim wątku oraz do zakończenia, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Operacja `StepOut` zostanie zakończona po powrocie z bieżącej ramki do ramki wywołującej.  
  
 Jeśli `StepOut` jest wywoływana w kodzie niezarządzanym, krok zakończy się, gdy bieżąca ramka powróci do zarządzanego kodu, który go wywołał.  
  
 W .NET Framework w wersji 2,0 nie należy używać `StepOut` z ustawioną flagą STOP_UNMANAGED, ponieważ zakończy się niepowodzeniem. (Użyj [ICorDebugStepper:: SetUnmappedStopMask —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) , aby ustawić flagi do wykonywania krokowo). Debugery międzyoperacyjności muszą przekroczyć kod natywny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
