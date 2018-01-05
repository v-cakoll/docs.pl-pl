---
title: "ICorProfilerInfo2::GetClassIDInfo2 — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassIDInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0348462cdbff14486b31e1878f06b7565b47182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 — Metoda
Pobiera moduł nadrzędny i metadanych token dla Otwórz ogólną definicję określonej klasy `ClassID` jego klasy nadrzędnej i `ClassID` dla każdego typu argumentu, jeśli jest obecny, klasy.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy, dla których zostaną pobrane informacje.  
  
 `pModuleId`  
 [out] Wskaźnik do Identyfikatora modułu nadrzędnego dla Otwórz ogólną definicję określonej klasy.  
  
 `pTypeDefToken`  
 [out] Wskaźnik do token metadanych dla Otwórz ogólną definicję określonej klasy.  
  
 `pParentClassId`  
 [out] Wskaźnik do Identyfikatora klasy nadrzędnej.  
  
 `cNumTypeArgs`  
 [in] Rozmiar `typeArgs` tablicy.  
  
 `pcNumTypeArgs`  
 [out] Wskaźnik do całkowitej liczby dostępnych elementów.  
  
 `typeArgs`  
 [out] Tablica `ClassID` wartości, z których każdy reprezentuje identyfikator argumentu typu klasy. Gdy metoda zwróci wartość, `typeArgs` będzie zawierał niektórych lub wszystkich dostępnych `ClassID` wartości.  
  
## <a name="remarks"></a>Uwagi  
 `GetClassIDInfo2` Metoda jest podobna do [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metody, ale `GetClassIDInfo2` uzyskuje dodatkowe informacje na temat typu ogólnego.  
  
 Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskanie [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu. Token metadanych, która jest zwracana do lokalizacji odwołuje się `pTypeDefToken` następnie może służyć do uzyskania dostępu do klasy metadanych.  
  
 Po `GetClassIDInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor był wystarczająco duży, aby pomieścić wszystkie `ClassID` wartości. W tym celu należy porównać wartości który `pcNumTypeArgs` wskazuje wartość `cNumTypeArgs` parametru. Jeśli `pcNumTypeArgs` wskazuje wartość, która jest większa niż `cNumTypeArgs`, Przydziel większy `typeArgs` buforu, zaktualizuj `cNumTypeArgs` z nowej, większy rozmiar i wywołanie `GetClassIDInfo2` ponownie.  
  
 Alternatywnie można wywołać `GetClassIDInfo2` o zerowej długości `typeArgs` buforu w celu uzyskania rozmiar buforu poprawne. Następnie można ustawić `typeArgs` rozmiar wartość zwracana w buforu `pcNumTypeArgs` i Wywołaj `GetClassIDInfo2` ponownie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
