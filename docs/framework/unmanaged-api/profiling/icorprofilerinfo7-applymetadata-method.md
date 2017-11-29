---
title: "ICorProfilerInfo7::ApplyMetaData — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ICorProfilerInfo7.ApplyMetaData
api_location: mscorwks.dll
api_type: COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e3724555df58392e5ab59ccb4f52dd2de860b8d4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7::ApplyMetaData — metoda
[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]  
  
 Stosuje metadane wynika z nowo `IMetadataEmit::Define*` metody do określonego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] Identyfikator modułu, którego metadanych został zmieniony.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli zmiany metadanych są wykonywane po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego, tej metody należy wywołać przed rozpoczęciem korzystania z nowymi metadanymi.  
  
 `ApplyMetaData`obsługuje tylko następujące typy metadanych dodawanie:  
  
-   `AssemblyRef`rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). Metoda.  
  
-   `TypeRef`rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metody.  
  
-   `TypeSpec`rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.  
  
-   `MemberRef`rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody.  
  
-   `MemberSpec`rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metody.  
  
-   `UserString`rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
