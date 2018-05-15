---
title: IMetaDataEmit::DeleteToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 269dac0f3d8a719224c177ef2c261e4c1e2e7e92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="b409d-102">IMetaDataEmit::DeleteToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="b409d-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="b409d-103">Usuwa określony token z bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="b409d-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b409d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b409d-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b409d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b409d-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="b409d-106">[in] Token do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="b409d-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b409d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b409d-107">Requirements</span></span>  
 <span data-ttu-id="b409d-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b409d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b409d-109">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b409d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b409d-110">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b409d-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b409d-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b409d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b409d-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b409d-112">See Also</span></span>  
 [<span data-ttu-id="b409d-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="b409d-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b409d-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b409d-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
