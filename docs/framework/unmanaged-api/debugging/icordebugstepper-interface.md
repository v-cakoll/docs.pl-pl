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
ms.openlocfilehash: 622fdfa37c93e406950e73941775828ae4b112fa
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379422"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper, interfejs
Reprezentuje krok wykonaniu kodu, który jest realizowany przez debuger; służy jako identyfikator między wydaniem i zakończeniem polecenia i zapewnia sposób anulowania kroku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Deactivate, metoda](icordebugstepper-deactivate-method.md)|Powoduje `ICorDebugStepper` , że zostanie anulowane odebrane polecenie ostatniego kroku.|  
|[IsActive — Metoda](icordebugstepper-isactive-method.md)|Pobiera wartość wskazującą, czy `ICorDebugStepper` aktualnie wykonuje krok.|  
|[SetInterceptMask, metoda](icordebugstepper-setinterceptmask-method.md)|Ustawia wartość CorDebugIntercept —, która określa typy kodu, do których nastąpi.|  
|[SetRangeIL, metoda](icordebugstepper-setrangeil-method.md)|Ustawia wartość wskazującą, czy wywołania [ICorDebugStepper:: StepRange —](icordebugstepper-steprange-method.md) przechodzą wartości argumentów względem kodu natywnego lub kodu języka pośredniego firmy Microsoft (MSIL) metody, która jest testowana przez.|  
|[SetUnmappedStopMask, metoda](icordebugstepper-setunmappedstopmask-method.md)|Ustawia wartość CorDebugUnmappedStop —, która określa typ niezamapowanego kodu, w którym wykonanie zostanie zatrzymane.|  
|[Step, metoda](icordebugstepper-step-method.md)|Powoduje, `ICorDebugStepper` że jest to jeden krok poprzez zawierający go wątek i opcjonalnie, aby kontynuować wykonywanie pojedynczej czynności przez funkcje, które są wywoływane w wątku.|  
|[StepOut, metoda](icordebugstepper-stepout-method.md)|Powoduje `ICorDebugStepper` , że jest to jeden krok za pomocą zawartego w nim wątku oraz do zakończenia, gdy bieżąca ramka zwraca sterowanie do ramki wywołującej.|  
|[StepRange, metoda](icordebugstepper-steprange-method.md)|Powoduje `ICorDebugStepper` , że jest to jeden krok przez zawierający go wątek i zwraca, gdy osiągnie kod poza ostatnim z określonych zakresów.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugStepper`Interfejs służy do następujących celów:  
  
- Pełni rolę identyfikatora między wydanym poleceniem kroku a ukończeniem tego polecenia.  
  
- Udostępnia centralny interfejs do hermetyzacji wszystkich kroków, które można wykonać.  
  
- Umożliwia przedwczesne anulowanie operacji wykonywania kroku.  
  
 Może istnieć więcej niż jeden stepper na wątek. Na przykład punkt przerwania może być trafiony podczas przechodzenia przez funkcję, a użytkownik może chcieć rozpocząć nową operację krokową w tej funkcji. Aby określić, jak obsługiwać tę sytuację, należy do debugera. Debuger może chcieć anulować pierwotną operację taktowania lub zagnieździć dwie operacje. `ICorDebugStepper`Interfejs obsługuje obie opcje.  
  
 Stepper może migrować między wątkami, jeśli środowisko uruchomieniowe języka wspólnego (CLR) wykonuje połączenie organizowane przez wiele wątków.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
