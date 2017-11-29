---
title: "ICorDebugStepper::StepRange — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72a68000691dd23a55b77265cae839bea8b4ae1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange — Metoda
Powoduje to ICorDebugStepper — aby pojedynczy krok za pomocą jego zawierającego wątku i zwracane w przypadku osiągnie kodu poza ostatniego z określonymi zakresami.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Ustaw `true` do kroku do funkcji, która jest wywoływana w wątku. Ustaw `false` do kroku przez funkcję.  
  
 `ranges`  
 [in] Tablica struktur COR_DEBUG_STEP_RANGE, z których każdy określa zakres.  
  
 `cRangeCount`  
 [in] Rozmiar `ranges` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `StepRange` Metody działa jak [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, z wyjątkiem tego, że nie zostanie ukończone do kodu zakres zostanie osiągnięty.  
  
 Może to być skuteczniejsze niż krokowe wykonywanie jednej instrukcji w czasie. Zakresy są określone jako lista par przesunięcia od początku stepper ramki.  
  
 Zakresy są względem kodu języka pośredniego (MSIL) firmy Microsoft metody. Wywołanie [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) z `false` aby zakresy względem kodu natywnego metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
