---
title: Metoda ICorProfilerInfo7::ApplyMetaData
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5caf7b5e24ac5e583420b45c563f53b8988f1e00
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332666"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="340d5-102">Metoda ICorProfilerInfo7::ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="340d5-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="340d5-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="340d5-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="340d5-104">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="340d5-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="340d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="340d5-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="340d5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="340d5-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="340d5-107">[in] Identyfikator modułu, którego metadanych został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="340d5-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="340d5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="340d5-108">Remarks</span></span>  
 <span data-ttu-id="340d5-109">Jeśli zmiany metadanych zostaną wprowadzone po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołanie zwrotne, tej metody należy wywołać przed rozpoczęciem korzystania z nowymi metadanymi.</span><span class="sxs-lookup"><span data-stu-id="340d5-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="340d5-110">`ApplyMetaData` obsługuje dodawanie tylko następujące typy metadanych:</span><span class="sxs-lookup"><span data-stu-id="340d5-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="340d5-111">`AssemblyRef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="340d5-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="340d5-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="340d5-112">method.</span></span>  
  
-   <span data-ttu-id="340d5-113">`TypeRef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="340d5-114">`TypeSpec` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="340d5-115">`MemberRef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="340d5-116">`MemberSpec` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="340d5-117">`UserString` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="340d5-118">Począwszy od .NET Core 3.0 to `ApplyMetaData` również obsługuje następujące typy:</span><span class="sxs-lookup"><span data-stu-id="340d5-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="340d5-119">`TypeDef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="340d5-120">`MethodDef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="340d5-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="340d5-121">Dodawanie metody wirtualne do istniejącego typu nie jest jednak obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="340d5-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="340d5-122">Metody wirtualne, należy dodać przed [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="340d5-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="340d5-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="340d5-123">Requirements</span></span>  
 <span data-ttu-id="340d5-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="340d5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="340d5-125">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="340d5-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="340d5-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="340d5-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="340d5-127">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="340d5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="340d5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="340d5-128">See also</span></span>
- [<span data-ttu-id="340d5-129">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="340d5-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
