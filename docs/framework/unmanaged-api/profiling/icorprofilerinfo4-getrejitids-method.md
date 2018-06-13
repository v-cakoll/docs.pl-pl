---
title: ICorProfilerInfo4::GetReJITIDs — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1055366576f45a7ca137b6d8170d1786c2ba4492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455344"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs — Metoda
Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie kompilowana JIT wersje określona funkcja nadal przydzielonych. Dotyczy to również ponownie kompilowana JIT wersje funkcji, które później przywrócić, ale nie została jeszcze uwolnione (na przykład, gdy domeny aplikacji, która zawiera funkcję przywróconego jest nadal używane).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] `FunctionID` Wystąpienia funkcji, dla którego wyliczyć wersji.  
  
 `cReJitIds`  
 [in] Liczba identyfikatorów ponownie kompilowana JIT przydzielone w `reJitIds` tablicy.  
  
 `pcReJitIds`  
 [out] Rzeczywista liczba identyfikatorów ponownie kompilowana JIT.  
  
 `reJitIds`  
 [out] Tablica przydzielone przez obiekt wywołujący, która będzie zawierać identyfikatory ponownie kompilowana JIT dla określonej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `GetReJITIDs` Wylicza aktywne identyfikatory ponownie kompilowana JIT dla wystąpienia danej funkcji. Wynika z tego samego wzorca użycia jak inne `ICorProfilerInfo` funkcje, które akceptują buforów przydzielone przez obiekt wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
