---
title: ICorProfilerInfo2::GetClassIDInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d58174aa8b8d0e0544566faa6b1d79c2c3d6197
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472619"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 — Metoda
Pobiera moduł nadrzędny i metadane token otwarte ogólne definicji określonej klasy `ClassID` klasy nadrzędnej, a `ClassID` dla każdego typu argumentu, jeśli jest obecny, klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy, dla którego będą pobierane informacje.  
  
 `pModuleId`  
 [out] Wskaźnik do Identyfikatora modułu nadrzędnego otwarte ogólne definicji określonej klasy.  
  
 `pTypeDefToken`  
 [out] Wskaźnik do tokenu metadanych otwarte ogólne definicji określonej klasy.  
  
 `pParentClassId`  
 [out] Wskaźnik do Identyfikatora klasy nadrzędnej.  
  
 `cNumTypeArgs`  
 [in] Rozmiar `typeArgs` tablicy.  
  
 `pcNumTypeArgs`  
 [out] Wskaźnik na całkowitą liczbę dostępnych elementów.  
  
 `typeArgs`  
 [out] Tablica `ClassID` wartości, z których każdy reprezentuje identyfikator argument typu klasy. Po powrocie z metody `typeArgs` będzie zawierać niektórych lub wszystkich dostępnych `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 `GetClassIDInfo2` Metoda jest podobna do [icorprofilerinfo::getclassidinfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metody, ale `GetClassIDInfo2` uzyskuje dodatkowe informacje na temat typu ogólnego.  
  
 Program profilujący kodu może wywołać [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu. Token metadanych, które są zwracane do lokalizacji, odwołuje się `pTypeDefToken` następnie może służyć do uzyskania dostępu do klasy metadanych.  
  
 Po `GetClassIDInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor jest wystarczająco duży, aby zawierała wszystkich `ClassID` wartości. Aby to zrobić, porównaj wartość która `pcNumTypeArgs` wskazuje z wartością `cNumTypeArgs` parametru. Jeśli `pcNumTypeArgs` wskazuje wartość, która jest większa niż `cNumTypeArgs`, Przydziel większego `typeArgs` buforu, zaktualizuj `cNumTypeArgs` przy użyciu nowych, większy rozmiar i Wywołaj `GetClassIDInfo2` ponownie.  
  
 Alternatywnie, można wywołać `GetClassIDInfo2` o zerowej długości `typeArgs` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić `typeArgs` rozmiar do wartości zwracanej w buforu `pcNumTypeArgs` i wywołać `GetClassIDInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
