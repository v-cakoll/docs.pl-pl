---
title: IMetaDataEmit::DeleteClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ad52580fef538a6878efb0febe41dec7c9de1de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520636"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="6ac39-102">IMetaDataEmit::DeleteClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="6ac39-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="6ac39-103">Niszczy podpisu metadanych układ klasy dla typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="6ac39-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ac39-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ac39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ac39-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6ac39-106">[in] `mdTypeDef` Token metadanych, który reprezentuje typ, dla którego układ klasy zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="6ac39-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac39-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ac39-107">Requirements</span></span>  
 <span data-ttu-id="6ac39-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ac39-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac39-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="6ac39-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ac39-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ac39-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ac39-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac39-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac39-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ac39-112">See also</span></span>
- [<span data-ttu-id="6ac39-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ac39-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6ac39-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ac39-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
