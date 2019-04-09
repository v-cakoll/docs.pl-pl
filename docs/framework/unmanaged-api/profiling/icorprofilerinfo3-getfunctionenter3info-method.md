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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8df3700c6002e7a181d4882c4afd8542c6b6c93a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164830"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
Zawiera informacje stosu ramki i argument funkcji, która jest zgłaszany do profilera za [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji. Ta metoda może być wywoływana tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] `FunctionID` Funkcji, która jest wprowadzanych.  
  
 `eltInfo`  
 [in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym. Program profilujący powinien udostępniać takie same `eltInfo` , zostało przekazane przez [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji.  
  
 `pFrameInfo`  
 [out] Dojście nieprzezroczyste reprezentujący typów ogólnych informacji na temat ramkę stosu w danym. Tego dojścia jest prawidłowy tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego, w którym profiler wywołał metodę `GetFunctionEnter3Info` metody.  
  
 `pcbArgumentInfo`  
 [out w] Wskaźnik do łączny rozmiar w bajtach, z [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury (oraz wszelkie dodatkowe [cor_prf_function_argument_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur dla zakresów argument wskazywany przez `pArgumentInfo`). Jeśli wybrany rozmiar nie jest wystarczająco dużo, zwracany jest ERROR_INSUFFICIENT_BUFFER i oczekiwany rozmiar jest przechowywany w `pcbArgumentInfo`. Aby wywołać `GetFunctionEnter3Info` tylko w celu pobrania z oczekiwaną wartością `*pcbArgumentInfo`ustaw `*pcbArgumentInfo`= 0 i `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) strukturę, która opisuje lokalizacje argumentów funkcji w pamięci, w kolejności od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący musi przydzielić wystarczającej ilości miejsca dla `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkcja, która jest poddawana i musi wskazywać wielkość w `pcbArgumentInfo` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
