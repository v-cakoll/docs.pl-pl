---
title: ICorDebugEval — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16beff67b4ef918afeb07ce4734fb8d2945e93c8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977204"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval — Interfejs

Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Przerywa obliczeń, to `ICorDebugEval` wykonuje obecnie obiektu.|  
|[CallFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Konfiguruje wywołanie do określonej funkcji. (Przestarzałe w wersji 2.0 .NET Framework; użyj [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) zamiast.)|  
|[CreateValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Pobiera wskaźnik interfejsu do określonego typu obiektu "ICorDebugValue" o wartości początkowej zero lub wartość null. (Przestarzałe w programie .NET Framework 2.0; użyj [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) zamiast.)|  
|[GetResult, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Pobiera wskaźnik interfejsu do `ICorDebugValue` zawierający wyniki obliczeń.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Pobiera wskaźnik interfejsu do "ICorDebugThread", gdzie tej oceny jest wykonywany lub zostanie wykonana.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugEval` obiekt jest w trakcie wykonywania.|  
|[NewArray, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Przydziela nową tablicę typu określonego elementu i wymiary. (Przestarzałe w programie .NET Framework 2.0; użyj [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) zamiast.)|  
|[NewObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Przydziela nowe wystąpienie obiektu, a następnie wywołuje metodę określonej konstruktora. (Przestarzałe w programie .NET Framework 2.0; użyj [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) zamiast.)|  
|[NewObjectNoConstructor, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Przydziela nowe wystąpienie obiektu określonego typu bez próby wywołania metody konstruktora. (Przestarzałe w programie .NET Framework 2.0; użyj [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) zamiast.)|  
|[NewString, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Przydziela obiekt ciągu przy użyciu określonej zawartości.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugEval` Obiekt jest tworzony w kontekście określonego wątku, który służy do przeprowadzania oceny. Wszystkie obiekty i typy używane w danej wersji ewaluacyjnej musi znajdować się w tej samej domenie aplikacji. Tej domeny aplikacji nie musi być taka sama jak bieżącej domeny aplikacji w wątku. Wersje ewaluacyjne mogą być zagnieżdżone.  
  
 Nie wykonuj operacje oceny do momentu wywołania debugera [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)i odbiera [ICorDebugManagedCallback::EvalComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) wywołania zwrotnego. Jeśli musisz korzystać z funkcji oceny to bez udzielania praw innych wątków, aby uruchomić wstrzymać wątków przy użyciu [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) lub [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Ponieważ kod użytkownika jest uruchomiona, gdy trwa obliczanie, wszystkie zdarzenia debugowania może wystąpić w tym klasy, ładowania i punktów przerwania. Debuger będzie odbierać wywołania zwrotne, zwykły dla tych zdarzeń. Stan oceny będą widoczne w ramach inspekcji stan programu normalny. Łańcuch stosu zostanie `CHAIN_FUNC_EVAL` łańcucha (Zobacz wyliczenie "cordebugstepreason —" i [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metody). Debuger pełny interfejs API, będą w dalszym ciągu działać w zwykły sposób.  
  
 W przypadku prawdopodobnie zakleszczone lub nieskończonej pętli sytuacji kod użytkownika nigdy nie może zostać zakończone. W takim przypadku należy wywołać [ICorDebugEval::Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) przed wznowieniem program.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także



- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
