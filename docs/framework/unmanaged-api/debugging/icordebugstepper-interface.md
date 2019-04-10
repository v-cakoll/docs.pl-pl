---
title: ICorDebugStepper, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212521"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper, interfejs
Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Deactivate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Powoduje to, że `ICorDebugStepper` ostatnie polecenie kroku otrzymał anulowania.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugStepper` jest w trakcie wykonywania kroku.|  
|[SetInterceptMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Ustawia wartość cordebugintercept —, który określa typy kodu, które zostaną wykorzystane do.|  
|[SetRangeIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Ustawia wartość wskazującą, czy wywołania [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przekazywanie wartości argumentu względem kodu natywnego lub kod intermediate language (MSIL) firmy Microsoft metody, która jest jest zmieniana za pośrednictwem.|  
|[SetUnmappedStopMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Ustawia wartość cordebugunmappedstop —, określający typ niezamapowane kodu, w którym wykonywanie zostanie zatrzymany.|  
|[Step, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Powoduje to, że `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku i, opcjonalnie, aby kontynuować, krokowe funkcje, które są wywoływane w wątku pojedynczego.|  
|[StepOut, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Powoduje to, że `ICorDebugStepper` krokowej za pośrednictwem jego zawierającego wątku i gdy zakończenie bieżącej ramki zwraca sterowanie do wywoływania ramki.|  
|[StepRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Powoduje to, że `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku, a także do zwrócenia, gdy osiągnie kod poza ostatnią z określonymi zakresami.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugStepper` Interfejsu służy do następujących celów:  
  
-   Działa ona jako identyfikator między polecenie kroku, wydawanego i wykonania tego polecenia.  
  
-   Go udostępnia interfejs centralny do hermetyzacji wszystkich przechodzenie krok po kroku, które mogą być wykonywane.  
  
-   Zapewnia sposób przedwcześnie anulowania operacji przechodzenia krok po kroku.  
  
 Może istnieć więcej niż jeden stepper na wątek. Na przykład może trafień punktu przerwania w wchodząc funkcji, a użytkownik może chcesz uruchomić nowej operacji przechodzenia krok po kroku wewnątrz tej funkcji. Jest debugera, aby określić sposób obsłużyć taką sytuację. Debuger może być zagnieździć dwóch operacji lub Anuluj operację przechodzenia krok po kroku. `ICorDebugStepper` Interfejs obsługuje obie te opcje.  
  
 Stepper mogą dokonać migracji między wątkami, jeśli wywołanie cross Threading, zorganizowanej sprawia, że środowisko uruchomieniowe języka wspólnego (CLR).  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
