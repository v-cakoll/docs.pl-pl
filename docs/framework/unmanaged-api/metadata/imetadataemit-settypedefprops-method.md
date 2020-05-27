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
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007770"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="faa1a-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="faa1a-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="faa1a-103">Ustawia funkcje typu zdefiniowanego przez poprzednie wywołanie [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="faa1a-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="faa1a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faa1a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="faa1a-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="faa1a-106">podczas `mdTypeDef`Token uzyskany od oryginalnego wywołania do [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="faa1a-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="faa1a-107">[w] `TypeDef` Attributes.</span><span class="sxs-lookup"><span data-stu-id="faa1a-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="faa1a-108">To jest maska bitów `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="faa1a-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="faa1a-109">podczas `mdToken`Klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="faa1a-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="faa1a-110">Uzyskano od poprzedniego wywołania do [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md)lub `null` .</span><span class="sxs-lookup"><span data-stu-id="faa1a-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="faa1a-111">podczas Tablica tokenów dla interfejsów, które implementuje ten typ.</span><span class="sxs-lookup"><span data-stu-id="faa1a-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="faa1a-112">Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::D efineimporttype](imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="faa1a-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="faa1a-113">Ostatni element tablicy musi być `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="faa1a-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa1a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="faa1a-114">Requirements</span></span>  
 <span data-ttu-id="faa1a-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa1a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa1a-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="faa1a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="faa1a-117">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="faa1a-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faa1a-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa1a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa1a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="faa1a-119">See also</span></span>

- [<span data-ttu-id="faa1a-120">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="faa1a-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="faa1a-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="faa1a-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
