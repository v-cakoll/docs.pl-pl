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
ms.openlocfilehash: a195daf2aa1b1c5a8f9c4335f7c4185f30093360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178532"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="a8545-102">IMetaDataEmit::DeleteClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="a8545-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="a8545-103">Niszczy podpisu metadanych układ klasy dla typu reprezentowanego przez określony token.</span><span class="sxs-lookup"><span data-stu-id="a8545-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8545-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8545-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8545-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a8545-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a8545-106">[in] `mdTypeDef` Token metadanych, który reprezentuje typ, dla którego układ klasy zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="a8545-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8545-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8545-107">Requirements</span></span>  
 <span data-ttu-id="a8545-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8545-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8545-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="a8545-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8545-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8545-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8545-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8545-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8545-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8545-112">See also</span></span>

- [<span data-ttu-id="a8545-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8545-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a8545-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8545-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
