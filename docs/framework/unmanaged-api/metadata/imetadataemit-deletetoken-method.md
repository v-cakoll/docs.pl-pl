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
ms.openlocfilehash: d85fb62936678f830ca7eaf26a97c36be5f23ac8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138245"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="90245-102">IMetaDataEmit::DeleteToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="90245-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="90245-103">Usuwa określony token z bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="90245-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90245-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90245-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90245-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90245-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="90245-106">[in] Token do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="90245-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90245-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90245-107">Requirements</span></span>  
 <span data-ttu-id="90245-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90245-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90245-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="90245-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90245-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="90245-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="90245-111">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="90245-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="90245-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90245-112">See also</span></span>

- [<span data-ttu-id="90245-113">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="90245-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="90245-114">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="90245-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
