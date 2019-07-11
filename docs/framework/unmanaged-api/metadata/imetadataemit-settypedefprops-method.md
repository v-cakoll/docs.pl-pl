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
ms.openlocfilehash: baee8566e923f9cb31868f8aa0e379ff1dfa42fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777224"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="6510a-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="6510a-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="6510a-103">Ustawia typ zdefiniowany przez wcześniejsze wywołanie funkcji [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="6510a-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6510a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6510a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6510a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6510a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6510a-106">[in] `mdTypeDef` Token uzyskany z wywołania oryginalnego [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="6510a-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6510a-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6510a-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6510a-108">Jest to z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="6510a-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6510a-109">[in] `mdToken` Klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="6510a-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="6510a-110">Uzyskany z poprzedniego wywołania [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), lub `null`.</span><span class="sxs-lookup"><span data-stu-id="6510a-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="6510a-111">[in] Tablica dla interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="6510a-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="6510a-112">Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="6510a-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="6510a-113">Ostatni element tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="6510a-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6510a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6510a-114">Requirements</span></span>  
 <span data-ttu-id="6510a-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6510a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6510a-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6510a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6510a-117">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6510a-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6510a-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6510a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6510a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6510a-119">See also</span></span>

- [<span data-ttu-id="6510a-120">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="6510a-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6510a-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6510a-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
