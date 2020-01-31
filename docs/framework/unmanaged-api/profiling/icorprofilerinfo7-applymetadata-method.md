---
title: 'ICorProfilerInfo7:: ApplyMetaData, Metoda'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861700"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7:: ApplyMetaData, Metoda
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Stosuje metadane nowo zdefiniowane przez metody `IMetadataEmit::Define*` do określonego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 podczas Identyfikator modułu, którego metadane zostały zmienione.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku wprowadzenia zmian metadanych po wywołaniu zwrotnym [ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) należy wywołać tę metodę przed użyciem nowych metadanych.  
  
 `ApplyMetaData` obsługuje tylko Dodawanie następujących typów metadanych:  
  
- `AssemblyRef` rekordy, które tworzysz, wywołując [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md). Method.  
  
- `TypeRef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .  
  
- `TypeSpec` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit:: GetTokenFromTypeSpec —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .  
  
- `MemberRef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .  
  
- `MemberSpec` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .  
  
- `UserString` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .  

Począwszy od platformy .NET Core 3,0, `ApplyMetaData` obsługuje również następujące typy:

- `TypeDef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .

- `MethodDef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) . Jednak dodawanie metod wirtualnych do istniejącego typu nie jest obsługiwane. Przed wywołaniem zwrotnym [ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) należy dodać metody wirtualne.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo7, interfejs](icorprofilerinfo7-interface.md)
