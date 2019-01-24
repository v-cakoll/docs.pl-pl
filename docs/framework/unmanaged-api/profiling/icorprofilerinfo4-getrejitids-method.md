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
ms.openlocfilehash: 6cb3a2235325533d5bd943a530a0a8e5b77100e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519947"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs — Metoda
Zwraca tablicę identyfikatorów, które identyfikują wszystkie ponownie skompilowana JIT wersje określonej funkcji, które nadal są przydzielane. Obejmuje to ponownie skompilowana JIT wersje funkcji, które następnie przywrócona, ale nie zostały jeszcze zwolnione (na przykład, gdy domeny aplikacji, która zawiera przywróconym funkcja jest nadal w użyciu).  
  
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
 [in] `FunctionID` Wystąpienia funkcji, do których chcesz wyliczyć wersji.  
  
 `cReJitIds`  
 [in] Liczba identyfikatorów ponownie skompilowana JIT, przydzielone w `reJitIds` tablicy.  
  
 `pcReJitIds`  
 [out] Rzeczywista liczba identyfikatorów ponownie skompilowana JIT.  
  
 `reJitIds`  
 [out] Tablica przydzielana przez obiekt wywołujący, który będzie zawierać identyfikatory ponownie skompilowana JIT dla określonej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `GetReJITIDs` Wylicza aktywne identyfikatory ponownie skompilowana JIT dla wystąpienia danej funkcji. Wynika z tego samego wzorca użycia, jak inne `ICorProfilerInfo` funkcje, które akceptują bufory przypisane do obiektu wywołującego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
