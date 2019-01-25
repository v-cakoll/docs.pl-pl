---
title: FunctionIDMapper — Funkcja
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d65d918147423396a18d2ea5c3edf7ff60c26a11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556132"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper — Funkcja
Powiadamia program profilujący, że identyfikator danej funkcji może być ponownie mapowany do alternatywnego Identyfikatora do użycia w [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) wywołań zwrotnych tej funkcji. `FunctionIDMapper` Umożliwia także profilującemu wskazanie, czy chce odbierać wywołania zwrotne do tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator funkcji ma być ponownie mapowany.  
  
 `pbHookFunction`  
 [out] Wskaźnik do wartości, która ustawia program profilujący `true` jeśli chce otrzymać `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołań zwrotnych; w przeciwnym wypadku ustawia tę wartość na `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Program profilujący zwraca wartość, której używa silnik wykonawczy jako identyfikatora alternatywnej funkcji. Zwracana wartość nie może mieć wartości null Jeśli nie `false` jest zwracany w `pbHookFunction`. W przeciwnym wypadku zwracana wartość null powoduje wygenerowanie produkuje nieoczekiwanych rezultatów, w tym ewentualnie powstrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 `FunctionIDMapper` Funkcja jest wywołanie zwrotne. Jest stosowana przez profiler, aby ponownie zamapować nazwę funkcji, aby inny identyfikator, który jest bardziej użyteczna w przypadku programu profilującego. `FunctionIDMapper` Zwraca alternatywny identyfikator służący do daną funkcję. Następnie aparat wykonywania honoruje żądania programu profilującego, przekazując to alternatywny identyfikator, oprócz identyfikator funkcji tradycyjnego, wróć do programu profilującego w `clientData` parametru `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` punkty zaczepienia do identyfikowania Funkcja, dla którego punkt zaczepienia jest wywoływana.  
  
 Możesz użyć [icorprofilerinfo::setfunctionidmapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metodę, aby określić implementację `FunctionIDMapper` funkcji. Możesz wywołać `ICorProfilerInfo::SetFunctionIDMapper` metody tylko raz, a firma Microsoft zaleca, aby zrobić to w [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
 Domyślnie, zakłada się, że program profilujący, ustawia flagę COR_PRF_MONITOR_ENTERLEAVE przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), i która określa punkty zaczepienia za pośrednictwem [icorprofilerinfo::setenterleavefunctionhooks —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) lub [icorprofilerinfo2::setenterleavefunctionhooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), powinien zostać wyświetlony `FunctionEnter2`, `FunctionLeave2`, i `FunctionTailcall2` wywołania zwrotne dla każdej funkcji. Jednak może wdrożyć profilery `FunctionIDMapper` zapobiegających selektywnego odbierania te wywołania zwrotne dla niektórych funkcji, ustawiając `pbHookFunction` do `false`.  
  
 Profilery powinien być odporny na błędy przypadków, gdy wiele wątków profilowana aplikacja wywołania dotyczą tej samej metody/funkcji jednocześnie. W takich przypadkach program profilujący może pojawić się wiele `FunctionIDMapper` wywołania zwrotne dla tego samego `FunctionID`. Program profilujący powinien być niektórych zwracać tej samej wartości z to wywołanie zwrotne, gdy jest wywoływana wiele razy z takimi samymi `FunctionID`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [SetFunctionIDMapper, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [FunctionIDMapper2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [FunctionEnter2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2, funkcja](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
