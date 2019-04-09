---
title: ICorProfilerInfo2::GetFunctionInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionInfo2
helpviewer_keywords:
- GetFunctionInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetFunctionInfo2 method [.NET Framework profiling]
ms.assetid: 0aa60f24-8bbd-4c83-83c5-86ad191b1d82
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b6c19c87aceffd1e199975db6f16191bc3ddd9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130276"
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 — Metoda
Pobiera klasy nadrzędnej, token metadanych i `ClassID` każdego argumentu typu, jeśli jest obecny w funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionInfo2(  
    [in]  FunctionID funcId,  
    [in]  COR_PRF_FRAME_INFO frameInfo,  
    [out] ClassID *pClassId,  
    [out] ModuleID *pModuleId,  
    [out] mdToken *pToken,  
    [in]  ULONG32 cTypeArgs,  
    [out] ULONG32 *pcTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator funkcji, dla którego należy pobrać element nadrzędny, klasy i inne informacje.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.  
  
 `pClassId`  
 [out] Wskaźnik do funkcji klasy nadrzędnej.  
  
 `pModuleId`  
 [out] Wskaźnik do modułu, w którym zdefiniowano funkcji klasy nadrzędnej.  
  
 `pToken`  
 [out] Wskaźnik do tokenu metadanych dla funkcji.  
  
 `cTypeArgs`  
 [in] Rozmiar `typeArgs` tablicy.  
  
 `pcTypeArgs`  
 [out] Wskaźnik do liczby całkowitej `ClassID` wartości.  
  
 `typeArgs`  
 [out] Tablica `ClassID` wartości, z których każdy jest Identyfikatorem argument typu funkcji. Po powrocie z metody `typeArgs` będzie zawierać części lub całości `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący kodu może wywołać [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu. Token metadanych, które są zwracane do lokalizacji, odwołuje się `pToken` następnie może służyć do uzyskania dostępu do funkcji metadanych.  
  
 Klasa identyfikator i typów argumentów, które są zwracane przez `pClassId` i `typeArgs` parametry są zależne od wartości, które zostały przekazane `frameInfo` parametru, jak pokazano w poniższej tabeli.  
  
|Wartość atrybutu `frameInfo` parametru|Wynik|  
|----------------------------------------|------------|  
|A `COR_PRF_FRAME_INFO` wartości, który został uzyskany z `FunctionEnter2` wywołania zwrotnego|`ClassID`, Są zwracane w lokalizacji odwołuje się `pClassId`, a następnie wpisz wszystkich argumentów i zwracanych w `typeArgs` tablicy, będzie dokładna.|  
|A `COR_PRF_FRAME_INFO` uzyskany ze źródła innego niż `FunctionEnter2` wywołania zwrotnego|Dokładnie `ClassID` i nie można określić argumentów typu. Oznacza to, że `ClassID` może mieć wartości null i mogą pochodzić niektórych argumentów typu jako <xref:System.Object>.|  
|Zero|Dokładnie `ClassID` i nie można określić argumentów typu. Oznacza to, że `ClassID` może mieć wartości null i mogą pochodzić niektórych argumentów typu jako <xref:System.Object>.|  
  
 Po `GetFunctionInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor jest wystarczająco duży, aby zawierała wszystkich `ClassID` wartości. Aby to zrobić, porównaj wartość która `pcTypeArgs` wskazuje z wartością `cTypeArgs` parametru. Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielonej przez rozmiar `ClassID` wartość, należy przydzielić większego `pcTypeArgs` buforu, zaktualizuj `cTypeArgs` przy użyciu nowych, większy rozmiar i Wywołaj `GetFunctionInfo2` ponownie.  
  
 Alternatywnie, można wywołać `GetFunctionInfo2` o zerowej długości `pcTypeArgs` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcTypeArgs` podzielonej przez rozmiar `ClassID` wartość i wywołania `GetFunctionInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
