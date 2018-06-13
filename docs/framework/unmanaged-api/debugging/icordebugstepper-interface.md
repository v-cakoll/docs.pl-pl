---
title: ICorDebugStepper — Interface1
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
ms.openlocfilehash: 339b823e5e9f38ffd175c79e379e28ccc3565c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423289"
---
# <a name="icordebugstepper-interface1"></a>ICorDebugStepper — Interface1
Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Deactivate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Powoduje to `ICorDebugStepper` anulować ostatnie odebrała polecenie kroku.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugStepper` jest w trakcie wykonywania kroku.|  
|[SetInterceptMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Ustawia wartość CorDebugIntercept, która określa typy kodu, które zostaną wykorzystane do.|  
|[SetRangeIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Ustawia wartość wskazującą, czy wywołań [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przekazać wartości argumentu względem kodu natywnego lub kod języka pośredniego (MSIL) firmy Microsoft metody, która jest trwa przeprowadził przez.|  
|[SetUnmappedStopMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Ustawia wartość CorDebugUnmappedStop, która określa typ Niemapowane kodu, w którym zostanie zatrzymanie wykonywania.|  
|[Step, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Powoduje to `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku oraz opcjonalnie można kontynuować krokowe funkcje, które są wywoływane w wątku pojedynczego.|  
|[StepOut, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Powoduje to `ICorDebugStepper` pojedynczy krok za pomocą jego zawierającego wątku i gdy zakończenie bieżącej ramki zwraca sterowania do wywoływania ramki.|  
|[StepRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Powoduje to `ICorDebugStepper` do pojedynczego kroku za pośrednictwem jego zawierającego wątku i zwracany, gdy osiągnie kodu poza ostatniego z określonymi zakresami.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugStepper` Interfejs służy do następujących celów:  
  
-   Działa ona jako identyfikator między wystawiony polecenie kroku i wykonanie tego polecenia.  
  
-   Zapewnia centralnego interfejsu hermetyzacji wszystkich stepping, które mogą być wykonywane.  
  
-   Zapewnia sposób przedwcześnie anulować operację wykonywania krokowego.  
  
 Może istnieć więcej niż jeden stepper na wątek. Na przykład punkt przerwania można napotkać podczas pominięcie funkcję, a użytkownik może chcesz uruchomić nowej operacji wykonywania krokowego wewnątrz tej funkcji. Jest debugera, aby określić sposób obsługi tej sytuacji. Debuger może być zagnieździć tych dwóch operacji lub Anuluj operację wykonywania krokowego. `ICorDebugStepper` Interfejs obsługuje obie te opcje.  
  
 Obiekt stepper może dokonać migracji między wątkami, jeśli środowisko uruchomieniowe języka wspólnego (CLR) nawiązuje połączenie między wątku, organizowane.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
