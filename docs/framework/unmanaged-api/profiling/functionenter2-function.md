---
title: "FunctionEnter2 — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter2
helpviewer_keywords: FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0aa1d98021dcbfc38721d7f30ad305065dced605
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter2-function"></a>FunctionEnter2 — Funkcja
Powiadamia profilera, czy formant jest przekazywany do funkcji i zawiera informacje o stosie argumenty ramki i funkcji. Ta funkcja zastępuje [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator funkcji, do którego jest przekazywany formantu.  
  
 `clientData`  
 [in] Identyfikator ponownie zmapowany funkcji, który profilera wcześniej określony za pomocą [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcji.  
  
 `func`  
 [in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.  
  
 Profiler należy potraktować jako nieprzezroczystego uchwyt, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) metody.  
  
 `argumentInfo`  
 [in] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury, która określa lokalizacje w pamięci argumentów funkcji.  
  
 Aby uzyskać dostęp do informacji argument `COR_PRF_ENABLE_FUNCTION_ARGS` musi zostać ustawiona flaga. Można użyć profilera [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody można ustawić flagi zdarzeń.  
  
## <a name="remarks"></a>Uwagi  
 Wartości `func` i `argumentInfo` parametry nie są prawidłowe po `FunctionEnter2` funkcja zwraca, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.  
  
 `FunctionEnter2` Funkcji jest wywołaniem zwrotnym; musisz go zaimplementować. Należy użyć implementacji `__declspec`(`naked`) atrybuty klasy magazynu.  
  
 Aparat wykonywania nie powoduje zapisania wszelkich rejestrów przed wywołaniem tej funkcji.  
  
-   Na wejściu musisz najpierw zapisać wszystkich rejestrów, których używasz, włączając jednostki liczb zmiennoprzecinkowych (FPU).  
  
-   Po zakończeniu należy przywrócić stosu przy wyświetlaniu Wyłącz wszystkie parametry, które zostały przekazane przez swojego obiektu wywołującego.  
  
 Implementacja `FunctionEnter2` nie należy zablokować, ponieważ spowoduje to opóźnienie wyrzucanie elementów bezużytecznych. Implementacja nie powinny podejmować wyrzucania elementów bezużytecznych, ponieważ stos nie mogą znajdować się w stanie przyjaznych dla kolekcji pamięci. Próbie wyrzucania elementów bezużytecznych do zablokuje środowiska uruchomieniowego `FunctionEnter2` zwraca.  
  
 Ponadto `FunctionEnter2` funkcji nie mogą wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób przydział pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Functionleave2 — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [Functiontailcall2 — funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Statyczne funkcje globalne profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
