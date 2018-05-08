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
ms.openlocfilehash: a864d8285c311a9d5c41a425f81678b294f0d8d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getfunctioninfo2-method"></a>ICorProfilerInfo2::GetFunctionInfo2 — Metoda
Pobiera klasy nadrzędnej, token metadanych i `ClassID` argumentu typu, jeśli jest obecny, funkcji.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator funkcji, dla którego można pobrać obiektu nadrzędnego, klasy i inne informacje.  
  
 `frameInfo`  
 [in] A `COR_PRF_FRAME_INFO` wartość, która wskazuje informacji na temat ramki stosu.  
  
 `pClassId`  
 [out] Wskaźnik do funkcji klasy nadrzędnej.  
  
 `pModuleId`  
 [out] Wskaźnik do modułu, w którym zdefiniowana jest klasa nadrzędna funkcji.  
  
 `pToken`  
 [out] Wskaźnik do tokenu metadanych dla funkcji.  
  
 `cTypeArgs`  
 [in] Rozmiar `typeArgs` tablicy.  
  
 `pcTypeArgs`  
 [out] Wskaźnik do łączna liczba `ClassID` wartości.  
  
 `typeArgs`  
 [out] Tablica `ClassID` wartości, z których każdy jest Identyfikatorem typem argumentu funkcji. Gdy metoda zwróci wartość, `typeArgs` będzie zawierał niektórych lub wszystkich `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskanie [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu. Token metadanych, która jest zwracana do lokalizacji odwołuje się `pToken` mogą następnie służyć do uzyskania dostępu do funkcji metadanych.  
  
 Klasa identyfikator i typ argumenty, które są zwracane przez `pClassId` i `typeArgs` parametry są zależne od wartości, który jest przekazywany w `frameInfo` parametru, jak pokazano w poniższej tabeli.  
  
|Wartość `frameInfo` parametru|Wynik|  
|----------------------------------------|------------|  
|A `COR_PRF_FRAME_INFO` wartości, który został uzyskany z `FunctionEnter2` wywołania zwrotnego|`ClassID`, Zwracane w lokalizacji odwołuje się `pClassId`, i wpisz wszystkich argumentów i zwracane w `typeArgs` tablicy, będą dokładne.|  
|A `COR_PRF_FRAME_INFO` uzyskany od źródła innego niż `FunctionEnter2` wywołania zwrotnego|Dokładnie `ClassID` i nie można określić argumentów typu. Oznacza to `ClassID` może mieć wartości null i niektórych argumentów typu może występować jako <xref:System.Object>.|  
|Zero|Dokładnie `ClassID` i nie można określić argumentów typu. Oznacza to `ClassID` może mieć wartości null i niektórych argumentów typu może występować jako <xref:System.Object>.|  
  
 Po `GetFunctionInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor był wystarczająco duży, aby pomieścić wszystkie `ClassID` wartości. W tym celu należy porównać wartości który `pcTypeArgs` wskazuje wartość `cTypeArgs` parametru. Jeśli `pcTypeArgs` wskazuje wartość, która jest większa niż `cTypeArgs` podzielonej przez rozmiar `ClassID` wartość, Przydziel większy `pcTypeArgs` buforu, zaktualizuj `cTypeArgs` z nowej, większy rozmiar i wywołanie `GetFunctionInfo2` ponownie.  
  
 Alternatywnie można wywołać `GetFunctionInfo2` o zerowej długości `pcTypeArgs` buforu w celu uzyskania rozmiar buforu poprawne. Rozmiar buforu można następnie ustawić wartość zwracana w `pcTypeArgs` podzielonej przez rozmiar `ClassID` wartość i wywołanie `GetFunctionInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
