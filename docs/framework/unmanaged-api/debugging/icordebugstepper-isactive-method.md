---
title: ICorDebugStepper::IsActive — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb276e6fba6a1b46b6be630804dc6f07c211b86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420511"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive — Metoda
Pobiera wartość wskazującą, czy ten ICorDebugStepper — obecnie wykonuje kroku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbActive`  
 [out] Zwraca `true` Jeśli stepper jest aktualnie wykonywany krok; w przeciwnym razie zwraca `false`.  
  
## <a name="remarks"></a>Uwagi  
 Dowolną akcję kroku pozostaje aktywna do momentu otrzymania przez debuger [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) wywołania, które automatycznie dezaktywuje stepper. Obiekt stepper może również zostaną wyłączone przedwcześnie wywołując [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) przed wywołania zwrotnego warunek zostanie osiągnięty.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
