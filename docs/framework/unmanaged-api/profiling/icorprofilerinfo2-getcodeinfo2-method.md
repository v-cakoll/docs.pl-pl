---
title: "ICorProfilerInfo2::GetCodeInfo2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetCodeInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b211ba79de7454361b44c6e9852ad6698c2e71c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 [in] Identyfikator funkcji, z którym jest skojarzona kodu natywnego.  
  
 `cCodeInfos`  
 [in] Rozmiar `codeInfos` tablicy.  
  
 `pcCodeInfos`  
 [out] Wskaźnik do łączna liczba [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury dostępne.  
  
 `codeInfos`  
 [out] Bufor podany przez obiekt wywołujący. Po powrocie z metody zawiera tablicę `COR_PRF_CODE_INFO` struktury, z których każdy zawiera opis blok kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Zakresy są sortowane w kolejności rosnącej przesunięcie język pośredni (MSIL) firmy Microsoft.  
  
 Po `GetCodeInfo2` zwróci wartość, należy sprawdzić, czy `codeInfos` bufor był wystarczająco duży, aby pomieścić wszystkie `COR_PRF_CODE_INFO` struktury. Aby to zrobić, porównanie wartości `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielonej przez rozmiar `COR_PRF_CODE_INFO` struktury jest mniejszy niż `pcCodeInfos`, Przydziel większy `codeInfos` buforu, zaktualizuj `cCodeInfos` z nowej, większy rozmiar i wywołanie `GetCodeInfo2` ponownie.  
  
 Alternatywnie można wywołać `GetCodeInfo2` o zerowej długości `codeInfos` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić `codeInfos` buforu rozmiar, aby wartość zwracana w `pcCodeInfos`, pomnożonych przez rozmiar `COR_PRF_CODE_INFO` struktury i wywołanie `GetCodeInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetCodeInfo3, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
