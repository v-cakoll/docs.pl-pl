---
title: ICorDebugStepper — Interfejs
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
ms.openlocfilehash: 3ca062231fd482c1f0d888935e882513461838ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137595"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper — Interfejs
Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Deactivate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|Powoduje, że ten `ICorDebugStepper` anuluje odebrane polecenie ostatniego kroku.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|Pobiera wartość wskazującą, czy ta `ICorDebugStepper` wykonuje obecnie krok.|  
|[SetInterceptMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|Ustawia wartość CorDebugIntercept —, która określa typy kodu, do których nastąpi.|  
|[SetRangeIL, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|Ustawia wartość wskazującą, czy wywołania [ICorDebugStepper:: StepRange —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) przechodzą wartości argumentów względem kodu natywnego lub kodu języka pośredniego firmy Microsoft (MSIL) metody, która jest testowana przez.|  
|[SetUnmappedStopMask, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|Ustawia wartość CorDebugUnmappedStop —, która określa typ niezamapowanego kodu, w którym wykonanie zostanie zatrzymane.|  
|[Step, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|Powoduje, że ten `ICorDebugStepper` jeden krok przez zawierający go wątek i opcjonalnie, aby kontynuować wykonywanie jednostopniowe za pomocą funkcji, które są wywoływane w wątku.|  
|[StepOut, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|Powoduje, że ten `ICorDebugStepper` przekroczenie jednego kroku przez zawierający go wątek i zakończenie, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.|  
|[StepRange, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|Powoduje, że ten `ICorDebugStepper` jeden krok przez zawierający go wątek i zwraca, gdy osiągnie kod poza ostatnim z określonych zakresów.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugStepper` służy do następujących celów:  
  
- Pełni rolę identyfikatora między wydanym poleceniem kroku a ukończeniem tego polecenia.  
  
- Udostępnia centralny interfejs do hermetyzacji wszystkich kroków, które można wykonać.  
  
- Umożliwia przedwczesne anulowanie operacji wykonywania kroku.  
  
 Może istnieć więcej niż jeden stepper na wątek. Na przykład punkt przerwania może być trafiony podczas przechodzenia przez funkcję, a użytkownik może chcieć rozpocząć nową operację krokową w tej funkcji. Aby określić, jak obsługiwać tę sytuację, należy do debugera. Debuger może chcieć anulować pierwotną operację taktowania lub zagnieździć dwie operacje. Interfejs `ICorDebugStepper` obsługuje obie opcje.  
  
 Stepper może migrować między wątkami, jeśli środowisko uruchomieniowe języka wspólnego (CLR) wykonuje połączenie organizowane przez wiele wątków.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
