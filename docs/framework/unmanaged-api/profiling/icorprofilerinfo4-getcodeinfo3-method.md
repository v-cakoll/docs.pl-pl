---
title: ICorProfilerInfo4::GetCodeInfo3 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 084007bd7ab20449c28d2c5e6125cbacfa280526
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912712"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 — Metoda
Pobiera zakresy kodu natywnego skojarzone z rekompilowaną ponownie wersją określonej funkcji JIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionID`  
 podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.  
  
 `reJitId`  
 podczas Tożsamość funkcji ponownie skompilowanej JIT.  
  
 `cCodeInfos`  
 podczas Rozmiar `codeInfos` tablicy.  
  
 `pcCodeInfos`  
 określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 określoną Bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy opisuje blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Metoda jest podobna do GetCodeInfo2 —, z tą różnicą, że zostanie pobrany identyfikator funkcji JIT-rekompilowany przez funkcję, która zawiera określony adres IP. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) `GetCodeInfo3`  
  
> [!NOTE]
> `GetCodeInfo3`może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [GetCodeInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nie będzie. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).  
  
 Po `GetCodeInfo3` powrocie należy sprawdzić `codeInfos` , czy bufor jest wystarczająco duży, aby można było zawierać wszystkie struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . W tym celu należy porównać wartość `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) jest `pcCodeInfos`mniejsza niż, Przydziel większy `codeInfos` bufor, zaktualizuj `cCodeInfos` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetCodeInfo3` .  
  
 Alternatywnie, można najpierw wywołać `GetCodeInfo3` z buforem o zerowej długości `codeInfos` , aby uzyskać prawidłowy rozmiar buforu. Następnie `codeInfos` można ustawić rozmiar buforu na wartość zwróconą `pcCodeInfos`w, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo3` .  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
