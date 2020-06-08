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
ms.openlocfilehash: 54e522aaaf23ae81b96b6be7168a9a13f28a16d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496142"
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
 określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 określoną Bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy opisuje blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 `GetCodeInfo3`Metoda jest podobna do [GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md), z tą różnicą, że zostanie pobrany identyfikator funkcji JIT-rekompilowany przez funkcję, która zawiera określony adres IP.  
  
> [!NOTE]
> `GetCodeInfo3`może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md) nie będzie. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).  
  
 Po `GetCodeInfo3` powrocie należy sprawdzić, czy `codeInfos` bufor jest wystarczająco duży, aby zawierał wszystkie struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . W tym celu należy porównać wartość `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) jest mniejsza niż `pcCodeInfos` , Przydziel większy `codeInfos` bufor, zaktualizuj `cCodeInfos` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetCodeInfo3` .  
  
 Alternatywnie, można najpierw wywołać `GetCodeInfo3` z buforem o zerowej długości, `codeInfos` Aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos` , pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) i `GetCodeInfo3` ponownie wywołać.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeInfo2, metoda](icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 — Interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
