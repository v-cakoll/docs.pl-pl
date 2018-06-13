---
title: ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c78d22c6566b49e85a59e4a682fa256d2d83ea3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455588"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
Udostępnia ramki stosu funkcji, która jest raportowany przez profiler [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkcji. Tę metodę można wywołać tylko podczas `FunctionTailcall3WithInfo` wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] `FunctionID` Funkcji, która zwraca.  
  
 `eltInfo`  
 [in] Nieprzezroczystego uchwyt reprezentujący informacji na temat ramka stosu danego. Profiler powinien zawierać takie same `eltInfo` który zostało przekazane do profilera przez `FunctionTailcall3WithInfo` funkcji.  
  
 `pFrameInfo`  
 [out] Nieprzezroczystego uchwyt reprezentujący informacje ogólne o ramka stosu danego. Ta dojścia jest prawidłowy tylko w trakcie `FunctionTailcall3WithInfo` wywołania zwrotnego o nazwie profilera `GetFunctionTailcall3Info` metody.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
