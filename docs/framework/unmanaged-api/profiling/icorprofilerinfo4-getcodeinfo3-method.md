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
ms.openlocfilehash: 164e042ab0f1a275ff07b917658024e22c2d7b0b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862039"
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
 podczas Rozmiar tablicy `codeInfos`.  
  
 `pcCodeInfos`  
 określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .  
  
 `codeInfos`  
 określoną Bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę struktur `COR_PRF_CODE_INFO`, z których każdy opisuje blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetCodeInfo3` jest podobna do [GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md), z tą różnicą, że otrzyma identyfikator funkcji JIT ponownie, która zawiera określony adres IP.  
  
> [!NOTE]
> `GetCodeInfo3` może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md) nie będzie. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).  
  
 Po powrocie `GetCodeInfo3` należy sprawdzić, czy bufor `codeInfos` był wystarczająco duży, aby zawierał wszystkie struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . W tym celu należy porównać wartość `cCodeInfos` z wartością parametru `cchName`. Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) jest mniejsza niż `pcCodeInfos`, Przydziel większy bufor `codeInfos`, zaktualizuj `cCodeInfos` z nowym, większym rozmiarem i ponownie wywołaj `GetCodeInfo3`.  
  
 Alternatywnie można najpierw wywołać `GetCodeInfo3` z buforem `codeInfos` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos`, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo3`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeInfo2, metoda](icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4, interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
