---
title: "FunctionIDMapper — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24e48ecb551a5faacc7da94b857b2e260f5aeca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper-function"></a>FunctionIDMapper — Funkcja
Powiadamia profilera, że danym identyfikatorem funkcji mogą być mapowane ponownie do alternatywny identyfikator ma być używany w [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołań zwrotnych dla tej funkcji. `FunctionIDMapper`Umożliwia również profilera wskazać, czy chce odbierać wywołań zwrotnych dla tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator funkcji można zamapować go ponownie.  
  
 `pbHookFunction`  
 [out] Wskaźnik do wartości, która ustawia profilera `true` jeśli chce otrzymywać `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Profiler zwraca wartość używaną przez aparat wykonywania jako identyfikator alternatywny funkcji. Wartość zwrotna nie może mieć wartości null chyba że `false` jest zwracany w `pbHookFunction`. W przeciwnym razie zwrócenie wartości null da nieoczekiwane wyniki, w tym prawdopodobnie zatrzymywanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 `FunctionIDMapper` Funkcja jest wywołaniem zwrotnym. Jest stosowana przez profiler ponownie zmapować Identyfikatora funkcji do innego identyfikatora, który jest bardziej użyteczna w przypadku profilera. `FunctionIDMapper` Zwraca alternatywny identyfikator służący do daną funkcję. Aparat wykonywania następnie honoruje żądania profiler od przekazania to alternatywny identyfikator jako uzupełnienie Identyfikatora tradycyjnych funkcja profilera w `clientData` parametr `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` punkty zaczepienia, aby zidentyfikować Funkcja, dla którego jest wywoływana haka.  
  
 Można użyć [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metodę, aby określić wykonania `FunctionIDMapper` funkcji. Możesz wywołać `ICorProfilerInfo::SetFunctionIDMapper` metody tylko raz i firma Microsoft zaleca, należy więc w [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
 Domyślnie zakłada się, że profiler który ustawia flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), i który ustawia punkty zaczepienia za pośrednictwem [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien zostać wyświetlony `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołań zwrotnych dla każdej funkcji. Jednak może wdrożyć profilery `FunctionIDMapper` Aby selektywnie uniknąć otrzymywania tych wywołań zwrotnych dla niektórych funkcji, ustawiając `pbHookFunction` do `false`.  
  
 Profilery powinien być odporny na błędy przypadków, gdzie wiele wątków profilowana aplikacja wywoływania tej samej metody/funkcja jednocześnie. W takich przypadkach profiler może pojawić się wiele `FunctionIDMapper` wywołań zwrotnych dla tego samego `FunctionID`. Profiler upewnij się zwrócić takie same wartości z tego wywołania zwrotnego przy wywołaniu wiele razy z tym samym `FunctionID`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [SetFunctionIDMapper, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [FunctionIDMapper2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
