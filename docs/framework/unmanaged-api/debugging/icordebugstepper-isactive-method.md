---
title: "ICorDebugStepper::IsActive — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25e4b59c59ee4340c14da22143f49c645e1dcc7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
