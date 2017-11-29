---
title: "ICorProfilerInfo4::GetCodeInfo3 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetCodeInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 87a93220bbaf3930f8ac2671efc0f19b2df8aee5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 — Metoda
Pobiera zakres skojarzone z ponownie kompilowana JIT wersja określona funkcja kodu natywnego.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `functionID`  
 [in] Identyfikator funkcji, z którym jest skojarzona kodu natywnego.  
  
 `reJitId`  
 [in] Tożsamość funkcja ponownie kompilowana JIT.  
  
 `cCodeInfos`  
 [in] Rozmiar `codeInfos` tablicy.  
  
 `pcCodeInfos`  
 [out] Wskaźnik do łączna liczba [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury dostępne.  
  
 `codeInfos`  
 [out] Bufor podany przez obiekt wywołujący. Po powrocie z metody zawiera tablicę `COR_PRF_CODE_INFO` struktury, z których każdy zawiera opis blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 `GetCodeInfo3` Metoda jest podobna do [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), ale pobierze ponownie kompilowana JIT identyfikator funkcję, która zawiera określony adres IP.  
  
> [!NOTE]
>  `GetCodeInfo3`może wyzwolić wyrzucania elementów bezużytecznych, podczas gdy [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nie. Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.  
  
 Zakresy są sortowane w kolejności zwiększenia przesunięcie wspólnego języka pośredniego (CIL).  
  
 Po `GetCodeInfo3` zwróci wartość, należy sprawdzić, czy `codeInfos` bufor był wystarczająco duży, aby pomieścić wszystkie [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury. Aby to zrobić, porównanie wartości `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielonej przez rozmiar [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury jest mniejszy niż `pcCodeInfos`, Przydziel większy `codeInfos` buforu, zaktualizuj `cCodeInfos` z nowej, większy rozmiar i wywołanie `GetCodeInfo3` ponownie.  
  
 Alternatywnie można wywołać `GetCodeInfo3` o zerowej długości `codeInfos` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić `codeInfos` buforu rozmiar, aby wartość zwracana w `pcCodeInfos`, pomnożonych przez rozmiar [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury i wywołanie `GetCodeInfo3` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetCodeInfo2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
 [ICorProfilerInfo4 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
