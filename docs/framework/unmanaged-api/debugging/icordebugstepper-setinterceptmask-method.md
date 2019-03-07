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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a9d287e6520f1fc7826d85dfbcd8e9a6da22f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481074"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask — Metoda
Ustawia wartość, która określa typy kodu, które zostaną wykorzystane do.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [in] Kombinacja wartości wyliczenia cordebugintercept —, który określa typy kodu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ustawiono bit interceptor, stepper zostanie ukończone, gdy zostanie osiągnięty danego typu przechwytuje kodu. Jeśli bit jest wyczyszczone, przechwytujący kod zostanie pominięte.  
  
 `SetInterceptMask` Metoda może mieć nieprzewidziane interakcji z [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z punktu widzenia użytkownika). Na przykład jeśli widoczne tylko dla (oznacza to, — wewnętrzny) część kodu inicjowania klasy brakuje informacji o mapowaniu i nie ustawiono STOP_NO_MAPPING_INFO (zobacz [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metody i Cordebugunmappedstop — wyliczenie), stepper przechodzi przez inicjowanie klasy. Domyślnie tylko INTERCEPT_NONE wartość `CorDebugIntercept` wyliczenie będą używane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
