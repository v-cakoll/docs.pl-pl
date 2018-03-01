---
title: "IMetaDataEmit::SetTypeDefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a03b781865b55b832b34bfdab7c88ce33f4e9e12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="f48ff-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f48ff-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="f48ff-103">Zestawy funkcji zdefiniowanych przez poprzednie wywołanie [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="f48ff-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f48ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f48ff-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f48ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f48ff-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f48ff-106">[in] `mdTypeDef` Tokenu uzyskanego z oryginalnego wywołania [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="f48ff-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="f48ff-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f48ff-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="f48ff-108">To jest maską bitów z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="f48ff-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="f48ff-109">[in] `mdToken` Klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f48ff-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="f48ff-110">Uzyskane z poprzedniego wywołania [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), lub `null`.</span><span class="sxs-lookup"><span data-stu-id="f48ff-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="f48ff-111">[in] Tablica dla interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="f48ff-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="f48ff-112">Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f48ff-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="f48ff-113">Jest ostatnim elemencie tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="f48ff-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f48ff-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f48ff-114">Requirements</span></span>  
 <span data-ttu-id="f48ff-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f48ff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f48ff-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f48ff-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f48ff-117">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f48ff-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f48ff-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f48ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48ff-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f48ff-119">See Also</span></span>  
 [<span data-ttu-id="f48ff-120">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f48ff-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f48ff-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f48ff-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
