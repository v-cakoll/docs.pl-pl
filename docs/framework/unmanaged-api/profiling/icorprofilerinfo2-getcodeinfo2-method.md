---
title: ICorProfilerInfo2::GetCodeInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 22463a56911354c9706bbfbc7d1824aee5d3c74d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725028"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 — Metoda
Pobiera zakres kodu natywnego skojarzonego z określonym `FunctionID`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionID`  
 [in] Identyfikator funkcji, z którą jest skojarzony kod macierzysty.  
  
 `cCodeInfos`  
 [in] Rozmiar `codeInfos` tablicy.  
  
 `pcCodeInfos`  
 [out] Wskaźnik do liczby całkowitej [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury dostępne.  
  
 `codeInfos`  
 [out] Bufor dostarczane przez obiekt wywołujący. Po powrocie z metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy zawiera opis bloku kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Zakresy są sortowane w kolejności rosnącej przesunięcia języka pośredniego (MSIL) firmy Microsoft.  
  
 Po `GetCodeInfo2` zwróci wartość, należy sprawdzić, czy `codeInfos` bufor jest wystarczająco duży, aby zawierała wszystkich `COR_PRF_CODE_INFO` struktury. Aby to zrobić, porównanie wartości `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielonej przez rozmiar `COR_PRF_CODE_INFO` struktury jest mniejszy niż `pcCodeInfos`, Przydziel większego `codeInfos` buforu, zaktualizuj `cCodeInfos` przy użyciu nowych, większy rozmiar i Wywołaj `GetCodeInfo2` ponownie.  
  
 Alternatywnie, można wywołać `GetCodeInfo2` o zerowej długości `codeInfos` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić `codeInfos` rozmiar do wartości zwracanej w buforu `pcCodeInfos`, pomnożone przez rozmiar `COR_PRF_CODE_INFO` struktury i wywołania `GetCodeInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [GetCodeInfo3, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
