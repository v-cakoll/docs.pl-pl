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
ms.openlocfilehash: ea66474e809b3813faceef79a69dd8a639a72a3b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502798"
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
 `GetFunctionFromIP2`jest podobny do `GetFunctionFromIP` , z tą różnicą, że pobiera identyfikator JIT-ponownie skompilowany zamiast identyfikatora funkcji funkcji, która zawiera określony adres IP.  
  
> [!NOTE]
> `GetFunctionFromIP2`może wyzwolić wyrzucanie elementów bezużytecznych, natomiast `GetFunctionFromIP` nie będzie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
