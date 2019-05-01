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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987431"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut — Metoda
Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku i ukończone, gdy bieżące ramce przekazuje sterowanie do wywoływania ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Uwagi  
 A `StepOut` operacja zakończy się po zwróceniu zwykle z bieżącej ramki do wywoływania ramki.  
  
 Jeśli `StepOut` jest wywoływana, gdy w kodzie niezarządzane, ten krok zostanie ukończone, gdy bieżące ramce powraca do kodu zarządzanego, który ją wywołuje.  
  
 W programie .NET Framework 2.0, nie należy używać `StepOut` z STOP_UNMANAGED flagą zestawu, ponieważ kończy się niepowodzeniem. (Użyj [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) można ustawić flagi do przechodzenia.) Debugery międzyoperacyjny musi Wyjdź do kodu macierzystego samodzielnie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
