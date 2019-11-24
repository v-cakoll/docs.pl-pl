---
title: ICorProfilerInfo::GetCodeInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 2393468f78312511d11cbe0ab422c26c710e25d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439227"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo — Metoda
Gets the extent of native code associated with the specified function ID.  
  
 This method is obsolete. Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] The ID of the function with which the native code is associated.  
  
 `pStart`  
 [out] A pointer to an array of bytes that compose the native code of the function.  
  
 `pcSize`  
 [out] A pointer to an integer that specifies the size, in bytes, of the native code.  
  
## <a name="remarks"></a>Uwagi  
 To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions. Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code. Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.  
  
 This function uses caller-allocated buffers.  
  
## <a name="requirements"></a>Wymagania  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** 1.0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
