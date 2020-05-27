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
ms.openlocfilehash: 3ef6b89ed6578d77f30d5e53657b962b200b0ed6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009327"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="54ee2-102">IMetaDataEmit::DeleteClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="54ee2-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="54ee2-103">Niszczy sygnaturę metadanych układu klasy dla typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="54ee2-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54ee2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54ee2-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54ee2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="54ee2-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="54ee2-106">podczas `mdTypeDef`Token metadanych reprezentujący typ, dla którego zostanie usunięty układ klasy.</span><span class="sxs-lookup"><span data-stu-id="54ee2-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54ee2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54ee2-107">Requirements</span></span>  
 <span data-ttu-id="54ee2-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54ee2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54ee2-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="54ee2-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54ee2-110">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="54ee2-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54ee2-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54ee2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54ee2-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54ee2-112">See also</span></span>

- [<span data-ttu-id="54ee2-113">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="54ee2-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="54ee2-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="54ee2-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
