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
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177461"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="96937-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="96937-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="96937-103">Ustawia funkcje typu zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="96937-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96937-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96937-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96937-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96937-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="96937-106">[w] Token `mdTypeDef` uzyskany z oryginalnego wywołania [do IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="96937-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="96937-107">[w] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="96937-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="96937-108">Jest to maska `CorTypeAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="96937-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="96937-109">[w] Klasa `mdToken` podstawowa.</span><span class="sxs-lookup"><span data-stu-id="96937-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="96937-110">Uzyskane z poprzedniego wywołania [do IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), lub `null`.</span><span class="sxs-lookup"><span data-stu-id="96937-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="96937-111">[w] Tablica tokenów dla interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="96937-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="96937-112">Tokeny te `mdTypeRef` są uzyskiwane przy użyciu [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="96937-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="96937-113">Ostatnim elementem tablicy musi `mdTokenNil`być .</span><span class="sxs-lookup"><span data-stu-id="96937-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96937-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96937-114">Requirements</span></span>  
 <span data-ttu-id="96937-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96937-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96937-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="96937-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96937-117">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96937-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96937-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96937-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96937-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96937-119">See also</span></span>

- [<span data-ttu-id="96937-120">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="96937-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="96937-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="96937-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
