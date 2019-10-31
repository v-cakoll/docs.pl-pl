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
ms.openlocfilehash: 00d9bef1e2b59a2d2207d1e343380e0e81bee848
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130353"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="3790d-102">ICorProfilerInfo7:: ApplyMetaData, Metoda</span><span class="sxs-lookup"><span data-stu-id="3790d-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="3790d-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="3790d-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="3790d-104">Stosuje metadane nowo zdefiniowane przez metody `IMetadataEmit::Define*` do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="3790d-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3790d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3790d-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3790d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="3790d-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="3790d-107">podczas Identyfikator modułu, którego metadane zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="3790d-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3790d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3790d-108">Remarks</span></span>  
 <span data-ttu-id="3790d-109">W przypadku wprowadzenia zmian metadanych po wywołaniu zwrotnym [ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) należy wywołać tę metodę przed użyciem nowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="3790d-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="3790d-110">`ApplyMetaData` obsługuje tylko Dodawanie następujących typów metadanych:</span><span class="sxs-lookup"><span data-stu-id="3790d-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="3790d-111">`AssemblyRef` rekordy, które tworzysz, wywołując [IMetaDataAssemblyEmit::D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="3790d-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="3790d-112">Method.</span><span class="sxs-lookup"><span data-stu-id="3790d-112">method.</span></span>  
  
- <span data-ttu-id="3790d-113">`TypeRef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="3790d-114">`TypeSpec` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit:: GetTokenFromTypeSpec —](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="3790d-115">`MemberRef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="3790d-116">`MemberSpec` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="3790d-117">`UserString` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="3790d-118">Począwszy od platformy .NET Core 3,0, `ApplyMetaData` obsługuje również następujące typy:</span><span class="sxs-lookup"><span data-stu-id="3790d-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="3790d-119">`TypeDef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="3790d-120">`MethodDef` rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3790d-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="3790d-121">Jednak dodawanie metod wirtualnych do istniejącego typu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="3790d-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="3790d-122">Przed wywołaniem zwrotnym [ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) należy dodać metody wirtualne.</span><span class="sxs-lookup"><span data-stu-id="3790d-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="3790d-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3790d-123">Requirements</span></span>  
 <span data-ttu-id="3790d-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3790d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3790d-125">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3790d-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3790d-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3790d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3790d-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3790d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3790d-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3790d-128">See also</span></span>

- [<span data-ttu-id="3790d-129">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="3790d-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
