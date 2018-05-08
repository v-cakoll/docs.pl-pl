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
ms.openlocfilehash: c2d282e27ec5068fa6fe7f58ba95458fdc219972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step — Metoda
Powoduje to ICorDebugStepper — do pojedynczego kroku za pośrednictwem jego zawierającego wątku oraz opcjonalnie można kontynuować krokowe funkcje, które są wywoływane w wątku pojedynczego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Ustaw `true` do kroku do funkcji, która jest wywoływana w wątku. Ustaw `false` do kroku przez funkcję.  
  
## <a name="remarks"></a>Uwagi  
 Krok działanie jest kończone po środowisko uruchomieniowe języka wspólnego wykonuje następną instrukcję zarządzanych w tym stepper ramki. Jeśli `Step` jest wywoływana na stepper, która nie jest w kod zarządzany, kroku zostanie zakończony podczas następnej instrukcji kod zarządzany jest wykonywany przez wątek.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
