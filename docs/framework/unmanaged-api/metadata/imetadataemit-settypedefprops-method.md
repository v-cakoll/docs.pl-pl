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
ms.openlocfilehash: ddb40c3265b3f42514d9dbd6f620a783089a4fad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481190"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="91ca6-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="91ca6-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="91ca6-103">Ustawia typ zdefiniowany przez wcześniejsze wywołanie funkcji [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="91ca6-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ca6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91ca6-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91ca6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="91ca6-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="91ca6-106">[in] `mdTypeDef` Token uzyskany z wywołania oryginalnego [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="91ca6-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="91ca6-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="91ca6-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="91ca6-108">Jest to z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="91ca6-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="91ca6-109">[in] `mdToken` Klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="91ca6-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="91ca6-110">Uzyskany z poprzedniego wywołania [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), lub `null`.</span><span class="sxs-lookup"><span data-stu-id="91ca6-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="91ca6-111">[in] Tablica dla interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="91ca6-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="91ca6-112">Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="91ca6-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="91ca6-113">Ostatni element tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="91ca6-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ca6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91ca6-114">Requirements</span></span>  
 <span data-ttu-id="91ca6-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91ca6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91ca6-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="91ca6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="91ca6-117">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="91ca6-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91ca6-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91ca6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ca6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91ca6-119">See also</span></span>
- [<span data-ttu-id="91ca6-120">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="91ca6-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="91ca6-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="91ca6-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
