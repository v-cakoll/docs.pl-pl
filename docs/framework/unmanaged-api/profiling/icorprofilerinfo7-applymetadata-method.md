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
ms.openlocfilehash: c30206145d08a22af49c4a6a0dc83fd7382bcc06
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495512"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="d6116-102">ICorProfilerInfo7:: ApplyMetaData, Metoda</span><span class="sxs-lookup"><span data-stu-id="d6116-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="d6116-103">[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="d6116-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="d6116-104">Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody do określonego modułu.</span><span class="sxs-lookup"><span data-stu-id="d6116-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6116-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6116-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6116-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6116-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d6116-107">podczas Identyfikator modułu, którego metadane zostały zmienione.</span><span class="sxs-lookup"><span data-stu-id="d6116-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6116-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6116-108">Remarks</span></span>  
 <span data-ttu-id="d6116-109">W przypadku wprowadzenia zmian metadanych po wywołaniu zwrotnym [ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) należy wywołać tę metodę przed użyciem nowych metadanych.</span><span class="sxs-lookup"><span data-stu-id="d6116-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="d6116-110">`ApplyMetaData`obsługuje tylko Dodawanie następujących typów metadanych:</span><span class="sxs-lookup"><span data-stu-id="d6116-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="d6116-111">`AssemblyRef`rekordy, które tworzysz, wywołując [IMetaDataAssemblyEmit::D efineassemblyref](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span><span class="sxs-lookup"><span data-stu-id="d6116-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="d6116-112">Method.</span><span class="sxs-lookup"><span data-stu-id="d6116-112">method.</span></span>  
  
- <span data-ttu-id="d6116-113">`TypeRef`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="d6116-114">`TypeSpec`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit:: GetTokenFromTypeSpec —](../metadata/imetadataemit-gettokenfromtypespec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="d6116-115">`MemberRef`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinememberref](../metadata/imetadataemit-definememberref-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="d6116-116">`MemberSpec`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit2::D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="d6116-117">`UserString`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efineuserstring](../metadata/imetadataemit-defineuserstring-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="d6116-118">Począwszy od platformy .NET Core 3,0, `ApplyMetaData` obsługiwane są również następujące typy:</span><span class="sxs-lookup"><span data-stu-id="d6116-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="d6116-119">`TypeDef`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="d6116-120">`MethodDef`rekordy, które tworzysz, wywołując metodę [IMetaDataEmit::D efinemethod](../metadata/imetadataemit-definemethod-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d6116-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="d6116-121">Jednak dodawanie metod wirtualnych do istniejącego typu nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d6116-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="d6116-122">Przed wywołaniem zwrotnym [ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) należy dodać metody wirtualne.</span><span class="sxs-lookup"><span data-stu-id="d6116-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6116-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6116-123">Requirements</span></span>  
 <span data-ttu-id="d6116-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6116-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6116-125">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d6116-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6116-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d6116-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6116-127">**.NET Framework wersje:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6116-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6116-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6116-128">See also</span></span>

- [<span data-ttu-id="d6116-129">ICorProfilerInfo7, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6116-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
