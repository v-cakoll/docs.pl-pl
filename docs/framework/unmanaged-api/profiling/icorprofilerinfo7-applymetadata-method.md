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
ms.openlocfilehash: aff6f63bb9f41fe45b22854787667070929bf987
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213769"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="e5b5a-102">Metoda ICorProfilerInfo7::ApplyMetaData</span><span class="sxs-lookup"><span data-stu-id="e5b5a-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="e5b5a-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e5b5a-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="e5b5a-104">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b5a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5b5a-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5b5a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5b5a-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="e5b5a-107">[in] Identyfikator modułu, którego metadanych został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5b5a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5b5a-108">Remarks</span></span>  
 <span data-ttu-id="e5b5a-109">Jeśli zmiany metadanych zostaną wprowadzone po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołanie zwrotne, tej metody należy wywołać przed rozpoczęciem korzystania z nowymi metadanymi.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 `ApplyMetaData` <span data-ttu-id="e5b5a-110">obsługuje dodawanie tylko następujące typy metadanych:</span><span class="sxs-lookup"><span data-stu-id="e5b5a-110">only supports adding the following types of metadata:</span></span>  
  
-   `AssemblyRef` <span data-ttu-id="e5b5a-111">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="e5b5a-111">records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="e5b5a-112">Metoda.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-112">method.</span></span>  
  
-   `TypeRef` <span data-ttu-id="e5b5a-113">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-113">records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
-   `TypeSpec` <span data-ttu-id="e5b5a-114">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-114">records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
-   `MemberRef` <span data-ttu-id="e5b5a-115">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-115">records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
-   `MemberSpec` <span data-ttu-id="e5b5a-116">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-116">records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
-   `UserString` <span data-ttu-id="e5b5a-117">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-117">records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="e5b5a-118">Począwszy od .NET Core 3.0 to `ApplyMetaData` również obsługuje następujące typy:</span><span class="sxs-lookup"><span data-stu-id="e5b5a-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- `TypeDef` <span data-ttu-id="e5b5a-119">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-119">records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- `MethodDef` <span data-ttu-id="e5b5a-120">rekordy, które możesz utworzyć przez wywołanie metody [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-120">records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="e5b5a-121">Dodawanie metody wirtualne do istniejącego typu nie jest jednak obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="e5b5a-122">Metody wirtualne, należy dodać przed [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e5b5a-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5b5a-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5b5a-123">Requirements</span></span>  
 <span data-ttu-id="e5b5a-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b5a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b5a-125">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5b5a-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5b5a-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5b5a-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e5b5a-127">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e5b5a-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5b5a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5b5a-128">See also</span></span>

- [<span data-ttu-id="e5b5a-129">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5b5a-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
