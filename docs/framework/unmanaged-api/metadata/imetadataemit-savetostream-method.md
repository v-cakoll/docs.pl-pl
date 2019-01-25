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
ms.openlocfilehash: 515e925c9b086823450b73cfbb558d0409b4948a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576002"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="82d0a-102">IMetaDataEmit::SaveToStream — Metoda</span><span class="sxs-lookup"><span data-stu-id="82d0a-102">IMetaDataEmit::SaveToStream Method</span></span>
<span data-ttu-id="82d0a-103">Zapisuje wszystkie metadane w bieżącym zakresie określonej `IStream`.</span><span class="sxs-lookup"><span data-stu-id="82d0a-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="82d0a-104">Syntax</span></span>  
  
```  
HRESULT SaveToStream (   
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82d0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82d0a-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="82d0a-106">[in] Strumień możliwy do zapisania, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="82d0a-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="82d0a-107">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="82d0a-107">[in] Reserved.</span></span> <span data-ttu-id="82d0a-108">Musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="82d0a-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d0a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82d0a-109">Requirements</span></span>  
 <span data-ttu-id="82d0a-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d0a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d0a-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="82d0a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82d0a-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82d0a-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82d0a-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82d0a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d0a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82d0a-114">See also</span></span>
- [<span data-ttu-id="82d0a-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="82d0a-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="82d0a-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="82d0a-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
