---
title: ICorProfilerInfo3::GetFunctionLeave3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionLeave3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionLeave3Info
helpviewer_keywords:
- GetFunctionLeave3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionLeave3Info method [.NET Framework profiling]
ms.assetid: df7083d2-fd43-44c7-9ce5-912c25cef0ff
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6470bd04e3661e7d27798747abc4ef0757bf4f1e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782153"
---
# <a name="icorprofilerinfo3getfunctionleave3info-method"></a>ICorProfilerInfo3::GetFunctionLeave3Info — Metoda
Udostępnia ramki stosu i wartość zwracana przez funkcję, która jest zgłaszany do profilera za [functionleave3withinfo — funkcja](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji. Ta metoda może być wywoływana tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionLeave3Info(  
            [in]  FunctionID functionId,  
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [out] COR_PRF_FUNCTION_ARGUMENT_RANGE *pRetvalRange);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] `FunctionID` Funkcji, która zwraca.  
  
 `eltInfo`  
 [in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym. Program profilujący powinien udostępniać takie same `eltInfo` , zostało przekazane do profilera za [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) funkcji.  
  
 `pFrameInfo`  
 [out] Dojście nieprzezroczyste reprezentujący typów ogólnych informacji na temat ramkę stosu w danym. Tego dojścia jest prawidłowy tylko podczas `FunctionLeave3WithInfo` wywołania zwrotnego, w którym profiler wywołał metodę `GetFunctionLeave3Info` metody.  
  
 `pRetvalRange`  
 [out] Wskaźnik do [cor_prf_function_argument_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) strukturę, która zawiera wartość, która jest zwracana przez funkcję. Dostęp do informacji o wartości zwracanej, `COR_PRF_ENABLE_FUNCTION_RETVAL` musi zostać ustawiona flaga. Można użyć programu profilującego [icorprofilerinfo::seteventmask — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) można ustawić flagi zdarzenia.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
