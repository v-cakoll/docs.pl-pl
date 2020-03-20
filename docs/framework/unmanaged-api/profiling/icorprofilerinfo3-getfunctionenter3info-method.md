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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177023"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
Zawiera ramki stosu i argument informacji funkcji, która jest zgłaszana do profilera przez [FunctionEnter3WithInfo](functionenter3withinfo-function.md) funkcji. Tę metodę można wywołać `FunctionEnter3WithInfo` tylko podczas wywołania zwrotnego.  
  
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
 [w] Funkcja, `FunctionID` która jest wprowadzana.  
  
 `eltInfo`  
 [w] Nieprzezroczysty uchwyt, który reprezentuje informacje o danej ramce stosu. Profiler powinien zapewnić `eltInfo` taki sam, że został podany przez [FunctionEnter3WithInfo](functionenter3withinfo-function.md) funkcji.  
  
 `pFrameInfo`  
 [na zewnątrz] Nieprzezroczysty dojście reprezentujące ogólne informacje o danej ramce stosu. Ten dojście jest `FunctionEnter3WithInfo` prawidłowy tylko podczas wywołania zwrotnego, w którym profiler o nazwie `GetFunctionEnter3Info` metody.  
  
 `pcbArgumentInfo`  
 [w, na zewnątrz] Wskaźnik do całkowitego rozmiaru , w bajtach, [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury (plus wszelkie dodatkowe [struktury COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) dla zakresów argumentów wskazanych przez `pArgumentInfo`). Jeśli określony rozmiar nie wystarczy, ERROR_INSUFFICIENT_BUFFER jest zwracany, a `pcbArgumentInfo`oczekiwany rozmiar jest przechowywany w pliku . Aby `GetFunctionEnter3Info` wywołać tylko pobrać oczekiwaną wartość dla `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 i `pArgumentInfo`=NULL.  
  
 `pArgumentInfo`  
 [na zewnątrz] Wskaźnik do [struktury COR_PRF_FUNCTION_ARGUMENT_INFO,](cor-prf-function-argument-info-structure.md) który opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Profiler musi przydzielić wystarczającą `COR_PRF_FUNCTION_ARGUMENT_INFO` ilość miejsca dla struktury funkcji, która jest `pcbArgumentInfo` kontrolowana i musi wskazywać rozmiar w parametrze.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Functionenter3withinfo](functionenter3withinfo-function.md)
- [Functionleave3withinfo](functionleave3withinfo-function.md)
- [FunkcjaTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowania](index.md)
