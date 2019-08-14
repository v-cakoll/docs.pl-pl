---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 90246ade67f797c04f0da5d9a68dadb83e4ce418
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973706"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo, Metoda
  
 Pobiera informacje o metodach dynamicznych.
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, dla której mają zostać pobrane informacje.  

 `moduleId`  
 podczas Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.  
  
 `ppvSig`  
 określoną Wskaźnik do podpisu dla funkcji.  
  
 `pbSig`  
 określoną Wskaźnik do liczby bajtów dla sygnatury funkcji.
  
 `cchName`  
 podczas Maksymalny rozmiar `wszName` tablicy.
  
 `pcchName`  
 określoną Liczba znaków w `wszName` tablicy.

 `wszName` \
 określoną Tablica `WCHAR` , która jest nazwą funkcji (jeśli taka istnieje).
  
## <a name="remarks"></a>Uwagi  
 Niektóre metody, takie jak IL repliks lub LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API [IMetaDataImport](../metadata/imetadataimport-interface.md) i [IMetaDataImport2](../metadata/imetadataimport2-interface.md) . Takie metody mogą być napotkane przez program do zaprogramowania za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).

 Ten interfejs API może służyć do pobierania informacji o metodach dynamicznych, łącznie z przyjazną nazwą, jeśli jest dostępna.  
  

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [! UWZGLĘDNIj[net_current_v472plus](../../../../includes/net-current-v472plus.md)  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo8, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

