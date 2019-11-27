---
title: ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 7e93b92b0b0b4c44955ebc7dfb9d1eb875713c27
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449725"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
Dostarcza ramkę stosu i informacje o argumentach funkcji raportowanej do profilera przez funkcję [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) . Tę metodę można wywołać tylko w trakcie wywołania zwrotnego `FunctionEnter3WithInfo`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas `FunctionID` funkcji, która jest wprowadzana.  
  
 `eltInfo`  
 podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu. Profiler powinien podać ten sam `eltInfo`, który został podany przez funkcję [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) .  
  
 `pFrameInfo`  
 określoną Nieprzezroczyste dojście reprezentujące ogólne informacje dotyczące danej ramki stosu. To dojście jest prawidłowe tylko w trakcie wywołania zwrotnego `FunctionEnter3WithInfo`, w którym Profiler nazywa metodę `GetFunctionEnter3Info`.  
  
 `pcbArgumentInfo`  
 [in. out] Wskaźnik do łącznego rozmiaru (w bajtach) struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) (oraz wszelkich dodatkowych struktur [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) dla zakresów argumentów wskazywanych przez `pArgumentInfo`). Jeśli określony rozmiar jest za mały, ERROR_INSUFFICIENT_BUFFER jest zwracany, a oczekiwany rozmiar jest przechowywany w `pcbArgumentInfo`. Aby wywołać `GetFunctionEnter3Info` tylko w celu pobrania oczekiwanej wartości dla `*pcbArgumentInfo`, ustaw `*pcbArgumentInfo`= 0 i `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 określoną Wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) , który opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Profiler musi przydzielić wystarczającą ilość miejsca dla struktury `COR_PRF_FUNCTION_ARGUMENT_INFO` funkcji, która jest sprawdzana, i musi wskazywać rozmiar w parametrze `pcbArgumentInfo`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
