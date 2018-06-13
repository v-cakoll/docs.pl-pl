---
title: IMetaDataEmit::SaveToStream — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 656f5ee20e50ea9ac5c03711adfd0b8264fbcca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444961"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="19155-102">IMetaDataEmit::SaveToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="19155-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="19155-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego `IStream`.</span><span class="sxs-lookup"><span data-stu-id="19155-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19155-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19155-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19155-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19155-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="19155-106">[in] Strumień zapisywalny, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="19155-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="19155-107">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="19155-107">[in] Reserved.</span></span> <span data-ttu-id="19155-108">Musi być równy zero.</span><span class="sxs-lookup"><span data-stu-id="19155-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19155-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19155-109">Requirements</span></span>  
 <span data-ttu-id="19155-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19155-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19155-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="19155-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19155-112">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="19155-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19155-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19155-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19155-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19155-114">See Also</span></span>  
 [<span data-ttu-id="19155-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="19155-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="19155-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="19155-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
