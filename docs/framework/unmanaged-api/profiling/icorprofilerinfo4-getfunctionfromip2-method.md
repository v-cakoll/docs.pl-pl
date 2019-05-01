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
ms.openlocfilehash: 18099e6e658391d6dae7a666cd0cebefa5859b1a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971551"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 — Metoda
Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie skompilowana JIT funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Parametry  
 `ip`  
 [in] Wskaźnik instrukcji w kodzie zarządzanym.  
  
 `pFunctionId`  
 [out] Identyfikator funkcji.  
  
 `pReJitId`  
 [out] Tożsamość ponownie skompilowana JIT wersję funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `GetFunctionFromIP2` jest podobny do `GetFunctionFromIP`, chyba że otrzymuje identyfikator ponownie skompilowana JIT, zamiast Identyfikatora funkcji, funkcji, która zawiera określony adres IP.  
  
> [!NOTE]
>  `GetFunctionFromIP2` Możesz wyzwolić wyrzucania elementów bezużytecznych, natomiast `GetFunctionFromIP` nie będzie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
