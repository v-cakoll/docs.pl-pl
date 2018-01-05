---
title: "ICorProfilerInfo::GetModuleInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetModuleInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8309b57f2940805e23010feac17b6d37f1a58af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a>ICorProfilerInfo::GetModuleInfo — Metoda
Podany identyfikator modułu zwraca nazwę modułu i identyfikator zestawu nadrzędnego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, dla których zostaną pobrane informacje.  
  
 `ppBaseLoadAddress`  
 [out] Adres podstawowy, w którym ładowany jest moduł.  
  
 `cchName`  
 [in] Długość w znakach, z `szName` buforze.  
  
 `pcchName`  
 [out] Wskaźnik do całkowita liczba znaków nazwy pliku modułu, która jest zwracana.  
  
 `szName`  
 [out] Bufor dostarczane przez obiekt wywołujący znaków dwubajtowych. Gdy metoda zwróci wartość, ten bufor zawiera nazwę pliku modułu.  
  
 `pAssemblyId`  
 [out] Wskaźnik do Identyfikatora zestawu nadrzędnego modułu.  
  
## <a name="remarks"></a>Uwagi  
 Dynamiczne modułów `szName` parametr jest pustym ciągiem, a adres podstawowy jest 0 (zero).  
  
 Mimo że `GetModuleInfo` może zostać wywołana metoda, jak modułu o identyfikatorze istnieje, identyfikator zestawu nadrzędnego nie będą dostępne do momentu otrzymania przez profiler [ICorProfilerCallback::ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) wywołania zwrotnego.  
  
 Gdy `GetModuleInfo` zwróci wartość, należy sprawdzić, czy `szName` bufor był wystarczająco duży, aby zawierała Pełna nazwa pliku modułu. W tym celu należy porównać wartości który `pcchName` wskazuje wartość `cchName` parametru. Jeśli `pcchName` wskazuje wartość, która jest większa niż `cchName`, Przydziel większy `szName` buforu, zaktualizuj `cchName` z nowej, większy rozmiar i wywołanie `GetModuleInfo` ponownie.  
  
 Alternatywnie można wywołać `GetModuleInfo` o zerowej długości `szName` buforu w celu uzyskania rozmiar buforu poprawne. Rozmiar buforu można następnie ustawić wartość zwracana w `pcchName` i Wywołaj `GetModuleInfo` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)  
 [GetModuleInfo2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)
