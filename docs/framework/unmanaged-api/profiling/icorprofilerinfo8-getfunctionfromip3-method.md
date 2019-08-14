---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973703"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3, Metoda
  
  Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID. Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.    
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a>Parametry  
 `ip`  
 podczas Wskaźnik instrukcji w kodzie zarządzanym.  

 `pFunctionId`  
 określoną Identyfikator funkcji.  
  
 `pReJitId`  
 określoną Tożsamość funkcji ponownie skompilowanej w trybie JIT.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda działa w przypadku metod dynamicznych i niedynamicznych. Jest to nadzbiór [GetFunctionFromIP2 —](icorprofilerinfo4-getfunctionfromip2-method.md), który działa tylko w przypadku funkcji z metadanymi.
  

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [! UWZGLĘDNIj[net_current_v472plus](../../../../includes/net-current-v472plus.md)  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo8, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

