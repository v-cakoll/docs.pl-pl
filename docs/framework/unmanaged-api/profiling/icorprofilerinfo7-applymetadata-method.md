---
title: Metoda ICorProfilerInfo7::ApplyMetaData
ms.date: 03/30/2017
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
ms.openlocfilehash: 7209314f9cf3170ba0b577395a5134f9549475e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536571"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="7e21f-102">Metoda ICorProfilerInfo7::ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="7e21f-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="7e21f-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="7e21f-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="7e21f-104">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="7e21f-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e21f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7e21f-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e21f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e21f-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="7e21f-107">[in] Identyfikator modułu, którego metadanych został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7e21f-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e21f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e21f-108">Remarks</span></span>  
 <span data-ttu-id="7e21f-109">Jeśli zmiany metadanych zostaną wprowadzone po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołanie zwrotne, tej metody należy wywołać przed rozpoczęciem korzystania z nowymi metadanymi.</span><span class="sxs-lookup"><span data-stu-id="7e21f-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="7e21f-110">`ApplyMetaData` obsługuje dodawanie tylko następujące typy metadanych:</span><span class="sxs-lookup"><span data-stu-id="7e21f-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
-   <span data-ttu-id="7e21f-111">`AssemblyRef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="7e21f-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="7e21f-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="7e21f-112">method.</span></span>  
  
-   <span data-ttu-id="7e21f-113">`TypeRef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7e21f-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   <span data-ttu-id="7e21f-114">`TypeSpec` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7e21f-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   <span data-ttu-id="7e21f-115">`MemberRef` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7e21f-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   <span data-ttu-id="7e21f-116">`MemberSpec` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7e21f-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   <span data-ttu-id="7e21f-117">`UserString` rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7e21f-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e21f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e21f-118">Requirements</span></span>  
 <span data-ttu-id="7e21f-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e21f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e21f-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e21f-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e21f-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e21f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e21f-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e21f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e21f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7e21f-123">See also</span></span>
- [<span data-ttu-id="7e21f-124">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="7e21f-124">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
