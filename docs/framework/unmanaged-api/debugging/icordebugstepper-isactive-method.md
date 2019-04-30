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
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763753"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive — Metoda
Pobiera wartość wskazującą, czy ten ICorDebugStepper — jest w trakcie wykonywania kroku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbActive`  
 [out] Zwraca `true` Jeśli stepper jest w trakcie wykonywania kroku; w przeciwnym razie zwraca `false`.  
  
## <a name="remarks"></a>Uwagi  
 Akcja w kroku pozostaje aktywne, dopóki debuger nie otrzyma [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) wywołania, które automatycznie dezaktywuje stepper. Stepper może również zostaną wyłączone przedwcześnie przez wywołanie metody [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) przed wywołania zwrotnego warunek zostanie osiągnięty.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
