---
title: IMetaDataEmit::DeleteFieldMarshal — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e7ba2d6f143b6bbb9ddc5a056191e53f719bfeb1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643952"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="fd3e2-102">IMetaDataEmit::DeleteFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="fd3e2-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="fd3e2-103">Niszczy PInvoke marshaling podpisu metadanych dla obiektu odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="fd3e2-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd3e2-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fd3e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd3e2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="fd3e2-106">[in] `mdFieldDef` Lub `mdParamDef` token, który reprezentuje pole lub parametr, dla której chcesz usunąć organizowania podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="fd3e2-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd3e2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd3e2-107">Requirements</span></span>  
 <span data-ttu-id="fd3e2-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd3e2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd3e2-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fd3e2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd3e2-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fd3e2-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd3e2-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd3e2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3e2-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd3e2-112">See also</span></span>
- [<span data-ttu-id="fd3e2-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd3e2-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fd3e2-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fd3e2-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
