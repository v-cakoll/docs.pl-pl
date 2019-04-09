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
ms.openlocfilehash: cb067d16ef7f8177f979a083707f8c6ef36750c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145811"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 — Metoda
Pobiera zakres skojarzony z wersją określoną funkcję ponownie skompilowana JIT kodu natywnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Identyfikator funkcji, z którą jest skojarzony kod macierzysty.  
  
 `reJitId`  
 [in] Tożsamość funkcja ponownie skompilowana JIT.  
  
 `cCodeInfos`  
 [in] Rozmiar `codeInfos` tablicy.  
  
 `pcCodeInfos`  
 [out] Wskaźnik do liczby całkowitej [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury dostępne.  
  
 `codeInfos`  
 [out] Bufor dostarczane przez obiekt wywołujący. Po powrocie z metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy zawiera opis bloku kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 `GetCodeInfo3` Metoda jest podobna do [getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), chyba że uzyska ponownie skompilowana JIT identyfikator funkcji, która zawiera określony adres IP.  
  
> [!NOTE]
>  `GetCodeInfo3` Możesz wyzwolić wyrzucania elementów bezużytecznych, natomiast [getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nie będzie. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Zakresy są sortowane w celu zwiększenia przesunięcie wspólny język pośredni (CIL).  
  
 Po `GetCodeInfo3` zwróci wartość, należy sprawdzić, czy `codeInfos` bufor jest wystarczająco duży, aby zawierała wszystkich [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury. Aby to zrobić, porównanie wartości `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielonej przez rozmiar [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury jest mniejszy niż `pcCodeInfos`, Przydziel większego `codeInfos` buforu, zaktualizuj `cCodeInfos` przy użyciu nowych, większy rozmiar, a wywołanie `GetCodeInfo3` ponownie.  
  
 Alternatywnie, można wywołać `GetCodeInfo3` o zerowej długości `codeInfos` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić `codeInfos` rozmiar do wartości zwracanej w buforu `pcCodeInfos`, pomnożone przez rozmiar [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury i wywołania `GetCodeInfo3` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
