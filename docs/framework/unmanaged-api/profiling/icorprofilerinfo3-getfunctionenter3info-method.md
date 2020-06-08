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
ms.openlocfilehash: 876ae07a432bfa36a7d9f43ae6c32ec03d7d3289
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496597"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
Dostarcza ramkę stosu i informacje o argumentach funkcji raportowanej do profilera przez funkcję [FunctionEnter3WithInfo](functionenter3withinfo-function.md) . Tę metodę można wywołać tylko w trakcie `FunctionEnter3WithInfo` wywołania zwrotnego.  
  
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
 podczas `FunctionID`Funkcja, która jest wprowadzana.  
  
 `eltInfo`  
 podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu. Profiler powinien zapewnić taki sam `eltInfo` , który został podany przez funkcję [FunctionEnter3WithInfo](functionenter3withinfo-function.md) .  
  
 `pFrameInfo`  
 określoną Nieprzezroczyste dojście reprezentujące ogólne informacje dotyczące danej ramki stosu. To dojście jest prawidłowe tylko `FunctionEnter3WithInfo` w przypadku wywołania zwrotnego, w którym Profiler nazywa `GetFunctionEnter3Info` metodę.  
  
 `pcbArgumentInfo`  
 [in. out] Wskaźnik do łącznego rozmiaru (w bajtach) struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) (oraz wszelkich dodatkowych struktur [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) dla zakresów argumentów wskazywanych przez `pArgumentInfo` ). Jeśli określony rozmiar jest za mały, ERROR_INSUFFICIENT_BUFFER jest zwracany, a oczekiwany rozmiar jest przechowywany w `pcbArgumentInfo` . Aby wywoływać `GetFunctionEnter3Info` tylko w celu pobrania oczekiwanej wartości parametru `*pcbArgumentInfo` , Set `*pcbArgumentInfo` = 0 i `pArgumentInfo` = null.  
  
 `pArgumentInfo`  
 określoną Wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , który opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Profiler musi przydzielić wystarczającą ilość miejsca dla `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkcji, która jest sprawdzana, i musi wskazywać rozmiar w `pcbArgumentInfo` parametrze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
