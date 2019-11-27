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
ms.openlocfilehash: 3ab29fc8c983b354ad5088d26c547868940ec70a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447717"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="38ec9-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="38ec9-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="38ec9-103">Ustawia funkcje typu zdefiniowanego przez poprzednie wywołanie [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="38ec9-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38ec9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="38ec9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38ec9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="38ec9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="38ec9-106">podczas Token `mdTypeDef` uzyskany od oryginalnego wywołania do [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="38ec9-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="38ec9-107">[in] `TypeDef` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="38ec9-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="38ec9-108">To jest maska bitów wartości `CorTypeAttr`.</span><span class="sxs-lookup"><span data-stu-id="38ec9-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="38ec9-109">podczas `mdToken` klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="38ec9-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="38ec9-110">Uzyskano od poprzedniego wywołania do [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md)lub `null`.</span><span class="sxs-lookup"><span data-stu-id="38ec9-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="38ec9-111">podczas Tablica tokenów dla interfejsów, które implementuje ten typ.</span><span class="sxs-lookup"><span data-stu-id="38ec9-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="38ec9-112">Te tokeny `mdTypeRef` są uzyskiwane przy użyciu [IMetaDataEmit::D efineimporttype](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="38ec9-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="38ec9-113">Ostatni element tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="38ec9-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38ec9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38ec9-114">Requirements</span></span>  
 <span data-ttu-id="38ec9-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38ec9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38ec9-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="38ec9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="38ec9-117">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="38ec9-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38ec9-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38ec9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ec9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38ec9-119">See also</span></span>

- [<span data-ttu-id="38ec9-120">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="38ec9-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="38ec9-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="38ec9-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
