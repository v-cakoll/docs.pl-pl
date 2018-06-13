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
ms.openlocfilehash: c4fe3eec4940b57001b7734c581076388f8ba0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33456989"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 — Metoda
Mapuje wskaźnik instrukcji kodu zarządzanego do wersji ponownie kompilowana JIT funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ip`  
 [in] Wskaźnik instrukcji w kodzie zarządzanym.  
  
 `pFunctionId`  
 [out] Identyfikatorem funkcji.  
  
 `pReJitId`  
 [out] Tożsamość wersji ponownie kompilowana JIT funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `GetFunctionFromIP2` przypomina `GetFunctionFromIP`, ale pobiera identyfikator ponownie kompilowana JIT zamiast Identyfikatora funkcji funkcji, która zawiera określony adres IP.  
  
> [!NOTE]
>  `GetFunctionFromIP2` może wyzwolić wyrzucania elementów bezużytecznych, podczas gdy `GetFunctionFromIP` nie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
