---
title: ICorDebugStepper::Step — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760568"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step — Metoda
Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku i, opcjonalnie, aby kontynuować, krokowe funkcje, które są wywoływane w wątku pojedynczego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Ustaw `true` aby wejść do funkcji, która jest wywołana w wątku. Ustaw `false` do kroku za pośrednictwem funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Ten krok zostanie ukończone, gdy środowisko uruchomieniowe języka wspólnego wykonuje następnej instrukcji zarządzanych w ramce tego stepper. Jeśli `Step` jest wywoływana na stepper, który nie jest w kodu zarządzanego, ten krok zostanie ukończone, gdy następnej instrukcji kodu zarządzanego jest wykonywana przez wątek.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
