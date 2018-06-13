---
title: ICorDebugEval Interface1
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
ms.openlocfilehash: 3ceda938798ba03a9f178776c4cd9439456182c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423039"
---
# <a name="icordebugeval-interface1"></a>ICorDebugEval Interface1
Dostarcza metody umożliwiające debugerowi wykonywanie kodu w kontekście debugowanego kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Abort, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|Przerywa obliczenia to `ICorDebugEval` wykonuje obecnie obiektu.|  
|[CallFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|Konfiguruje wywołanie określonych funkcji. (Przestarzałe w programie .NET Framework w wersji 2.0, przy użyciu [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) zamiast.)|  
|[CreateValue, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|Pobiera wskaźnika interfejsu do określonego typu obiektu "ICorDebugValue" o wartości początkowej zero lub wartość null. (Przestarzałe w .NET Framework 2.0, przy użyciu [ICorDebugEval2::CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) zamiast.)|  
|[GetResult, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|Pobiera wskaźnika interfejsu do `ICorDebugValue` zawierającego wyniki oceny.|  
|[GetThread, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|Pobiera wskaźnika interfejsu do "ICorDebugThread", gdzie tej oceny jest wykonywany lub będą wykonywane.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugEval` obiektu jest aktualnie wykonywany.|  
|[NewArray, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|Przydziela nowej tablicy o typie określonym elemencie i wymiary. (Przestarzałe w .NET Framework 2.0, przy użyciu [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) zamiast.)|  
|[NewObject, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|Przydziela nowe wystąpienie obiektu i wywołuje metodę określony Konstruktor. (Przestarzałe w .NET Framework 2.0, przy użyciu [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) zamiast.)|  
|[NewObjectNoConstructor, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|Przydziela nowe wystąpienie obiektu określonego typu bez próba wywołania metody konstruktora. (Przestarzałe w .NET Framework 2.0, przy użyciu [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) zamiast.)|  
|[NewString, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|Przydziela obiekt ciągu przy użyciu określonej zawartości.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugEval` Obiekt jest tworzony w kontekście określonego wątku, który służy do przeprowadzania oceny. Wszystkie obiekty i typów używanych w danym oceny musi znajdować się w tej samej domenie aplikacji. Tej domeny aplikacji nie musi być taka sama, jak domena aplikacji bieżącego wątku. Mogą być zagnieżdżane oceny.  
  
 Do wywołania debugera nie są wykonywane operacje oceny [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md), a następnie odbiera [ICorDebugManagedCallback::EvalComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md) wywołania zwrotnego. Jeśli musisz korzystać z funkcji oceny bez zezwalania na innych wątków, aby uruchomić wstrzymać wątków za pomocą [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) lub [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md).  
  
 Ponieważ kod użytkownika jest uruchomiony, gdy trwa obliczanie, wszelkie zdarzenia debugowania mogą wystąpić, łącznie z klasy obciążeń i punktów przerwania. Debuger będzie odbierać wywołań zwrotnych, jak zwykle te zdarzenia. Stan oceny będą widoczne w ramach kontroli stanu normalnej program. Łańcuch stosu zostanie `CHAIN_FUNC_EVAL` łańcucha (Zobacz wyliczenie "CorDebugStepReason" i [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metody). Debuger pełnego interfejsu API będzie działać jak zwykle.  
  
 Kod użytkownika nigdy nie może zakończyć się w przypadku zakleszczenia lub nieskończonej pętli sytuacji. W takim przypadku należy wywołać [ICorDebugEval::Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) przed wznowieniem program.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
    
    
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
