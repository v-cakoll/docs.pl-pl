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
ms.openlocfilehash: f6d26abba649b608858fde8beaac750600493869
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442854"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs — Metoda
Zwraca tablicę identyfikatorów, które identyfikują wszystkie wersje JIT-ponownie skompilowane określonej funkcji, które są nadal przydzieleni. Obejmuje to ponowne skompilowane przez JIT wersje funkcji, które zostały później przywrócone, ale nie zostały jeszcze zwolnione (na przykład wtedy, gdy domena aplikacji zawierająca przywróconą funkcję jest nadal w użyciu).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas `FunctionID` wystąpienia funkcji, dla którego mają zostać wyliczone wersje.  
  
 `cReJitIds`  
 podczas Liczba identyfikatorów ponownych kompilacji JIT przypisywanych w tablicy `reJitIds`.  
  
 `pcReJitIds`  
 określoną Rzeczywista liczba identyfikatorów ponownych kompilacji JIT.  
  
 `reJitIds`  
 określoną Tablica przypisana przez obiekt wywołujący, która będzie zawierać identyfikatory ponownie skompilowane JIT dla określonej funkcji.  
  
## <a name="remarks"></a>Uwagi  
 `GetReJITIDs` wylicza aktywne ponownie skompilowane identyfikatory JIT dla danego wystąpienia funkcji. Jest on zgodny z tym samym wzorcem użycia co inne funkcje `ICorProfilerInfo`, które akceptują bufory przydzieloną przez obiekt wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
