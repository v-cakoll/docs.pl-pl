---
title: "FunctionLeave3WithInfo — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3WithInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3WithInfo
helpviewer_keywords: FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f787b5bd78a575d862c198daeee99a0704734276
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave3withinfo-function"></a>FunctionLeave3WithInfo — Funkcja
Powiadamia profilera, że formant zostały zwrócone z funkcji, a także uchwytu, które mogą zostać przekazane do [ICorProfilerInfo3::GetFunctionLeave3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) można pobrać ramki stosu oraz wartości zwracanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionIDOrClientID`  
 [in] Identyfikator funkcji zwróceniem sterowania.  
  
 `eltInfo`  
 [in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego. Ta dojścia jest prawidłowy tylko w trakcie wywołania zwrotnego, do którego jest przekazywany.  
  
## <a name="remarks"></a>Uwagi  
 `FunctionLeave3WithInfo` Metody wywołania zwrotnego powiadamia profilera funkcje są nazywane i pozwala profiler do użycia [ICorProfilerInfo3::GetFunctionLeave3Info — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) do zbadania wartości zwracanej. Dostęp do informacji zwracanej wartości, `COR_PRF_ENABLE_FUNCTION_RETVAL` flagi musi zostać ustawione. Profiler można użyć [ICorProfilerInfo::SetEventMask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) Ustaw flagi zdarzeń, a następnie użyć [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) do zarejestrowania użytkownika Implementacja tej funkcji.  
  
 `FunctionLeave3WithInfo` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować. Należy użyć implementacji `__declspec(naked)` atrybuty klasy magazynu.  
  
 Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.  
  
-   Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).  
  
-   Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.  
  
 Implementacja `FunctionLeave3WithInfo` nie zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych. Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci. Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionLeave3WithInfo` zwraca.  
  
 `FunctionLeave3WithInfo` Funkcji nie musi wywołania wewnątrz kodu zarządzanego lub spowodować przydział pamięci zarządzanej w dowolny sposób.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
