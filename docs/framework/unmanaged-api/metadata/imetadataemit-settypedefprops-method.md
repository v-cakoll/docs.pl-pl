---
title: IMetaDataEmit::SetTypeDefProps — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596888a8eb4a55c4cfe594b1911f17f6d32f56d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165935"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="5cab3-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="5cab3-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="5cab3-103">Ustawia typ zdefiniowany przez wcześniejsze wywołanie funkcji [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cab3-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cab3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5cab3-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cab3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5cab3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5cab3-106">[in] `mdTypeDef` Token uzyskany z wywołania oryginalnego [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cab3-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5cab3-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5cab3-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5cab3-108">Jest to z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="5cab3-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5cab3-109">[in] `mdToken` Klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="5cab3-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="5cab3-110">Uzyskany z poprzedniego wywołania [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), lub `null`.</span><span class="sxs-lookup"><span data-stu-id="5cab3-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="5cab3-111">[in] Tablica dla interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="5cab3-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="5cab3-112">Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="5cab3-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="5cab3-113">Ostatni element tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="5cab3-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cab3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5cab3-114">Requirements</span></span>  
 <span data-ttu-id="5cab3-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cab3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cab3-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5cab3-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5cab3-117">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5cab3-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5cab3-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5cab3-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5cab3-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cab3-119">See also</span></span>

- [<span data-ttu-id="5cab3-120">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5cab3-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5cab3-121">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5cab3-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
