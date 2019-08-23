---
title: ICorProfilerInfo4::GetFunctionFromIP2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c133338ec0edac19f49d435df41e3081c486f51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948462"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 — Metoda
Mapuje wskaźnik zarządzanej instrukcji kodu do wersji funkcji ponownie skompilowanej przez JIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Parametry  
 `ip`  
 podczas Wskaźnik instrukcji w kodzie zarządzanym.  
  
 `pFunctionId`  
 określoną Identyfikator funkcji.  
  
 `pReJitId`  
 określoną Tożsamość funkcji ponownie skompilowanej w trybie JIT.  
  
## <a name="remarks"></a>Uwagi  
 `GetFunctionFromIP2`jest podobny do `GetFunctionFromIP`, z tą różnicą, że pobiera identyfikator JIT-ponownie skompilowany zamiast identyfikatora funkcji funkcji, która zawiera określony adres IP.  
  
> [!NOTE]
> `GetFunctionFromIP2`może wyzwolić wyrzucanie elementów `GetFunctionFromIP` bezużytecznych, natomiast nie będzie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
