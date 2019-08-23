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
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962688"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper, interfejs
Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Deactivate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|`ICorDebugStepper` Powoduje, że zostanie anulowane odebrane polecenie ostatniego kroku.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Pobiera wartość wskazującą, czy `ICorDebugStepper` aktualnie wykonuje krok.|  
|[SetInterceptMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Ustawia wartość CorDebugIntercept —, która określa typy kodu, do których nastąpi.|  
|[SetRangeIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Ustawia wartość wskazującą, czy wywołania [ICorDebugStepper:: StepRange —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przechodzą wartości argumentów względem kodu natywnego lub kodu języka pośredniego firmy Microsoft (MSIL) metody, która jest testowana przez.|  
|[SetUnmappedStopMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Ustawia wartość CorDebugUnmappedStop —, która określa typ niezamapowanego kodu, w którym wykonanie zostanie zatrzymane.|  
|[Step, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Powoduje, `ICorDebugStepper` że jest to jeden krok poprzez zawierający go wątek i opcjonalnie, aby kontynuować wykonywanie pojedynczej czynności przez funkcje, które są wywoływane w wątku.|  
|[StepOut, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Powoduje, `ICorDebugStepper` że jest to jeden krok za pomocą zawartego w nim wątku oraz do zakończenia, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.|  
|[StepRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Powoduje, `ICorDebugStepper` że jest to jeden krok przez zawierający go wątek i zwraca, gdy osiągnie kod poza ostatnim z określonych zakresów.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugStepper` Interfejs służy do następujących celów:  
  
- Pełni rolę identyfikatora między wydanym poleceniem kroku a ukończeniem tego polecenia.  
  
- Udostępnia centralny interfejs do hermetyzacji wszystkich kroków, które można wykonać.  
  
- Umożliwia przedwczesne anulowanie operacji wykonywania kroku.  
  
 Może istnieć więcej niż jeden stepper na wątek. Na przykład punkt przerwania może być trafiony podczas przechodzenia przez funkcję, a użytkownik może chcieć rozpocząć nową operację krokową w tej funkcji. Aby określić, jak obsługiwać tę sytuację, należy do debugera. Debuger może chcieć anulować pierwotną operację taktowania lub zagnieździć dwie operacje. `ICorDebugStepper` Interfejs obsługuje obie opcje.  
  
 Stepper może migrować między wątkami, jeśli środowisko uruchomieniowe języka wspólnego (CLR) wykonuje połączenie organizowane przez wiele wątków.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
