---
title: "ICorProfilerInfo3::GetFunctionEnter3Info — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a75f76af924c3e75d280c36fb5f436498dc6c862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a>ICorProfilerInfo3::GetFunctionEnter3Info — Metoda
Zawiera informacje ramki i argument stosu funkcji, która jest raportowany przez profiler [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji. Tę metodę można wywołać tylko podczas `FunctionEnter3WithInfo` wywołania zwrotnego.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] `FunctionID` Funkcji, która jest wprowadzane.  
  
 `eltInfo`  
 [in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego. Profiler powinien zawierać takie same `eltInfo` który został udzielony przez [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkcji.  
  
 `pFrameInfo`  
 [out] Nieprzezroczystego uchwyt reprezentujący informacje ogólne o ramka stosu danego. Ta dojścia jest prawidłowy tylko w trakcie `FunctionEnter3WithInfo` wywołania zwrotnego o nazwie profilera `GetFunctionEnter3Info` metody.  
  
 `pcbArgumentInfo`  
 [w, out] Wskaźnik całkowity rozmiar w bajtach z [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury (oraz wszelkie dodatkowe [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur zakresów argument wskazywana przez `pArgumentInfo`). Jeśli określony rozmiar jest niewystarczający, zwracany jest ERROR_INSUFFICIENT_BUFFER i oczekiwanym rozmiarem są przechowywane w `pcbArgumentInfo`. Aby wywołać `GetFunctionEnter3Info` tylko w celu oczekiwanej wartości dla pobrania `*pcbArgumentInfo`ustaw `*pcbArgumentInfo`= 0 i `pArgumentInfo`= NULL.  
  
 `pArgumentInfo`  
 [out] Wskaźnik do [cor_prf_function_argument_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktury, która opisuje lokalizacje argumentów funkcji w pamięci w kolejności od lewej do prawej.  
  
## <a name="remarks"></a>Uwagi  
 Profiler musi przydzielić wystarczającą ilość miejsca na `COR_PRF_FUNCTION_ARGUMENT_INFO` struktury funkcji, która jest kontrolowanym i musi wskazywać rozmiar w `pcbArgumentInfo` parametru.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [ICorProfilerInfo3 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
