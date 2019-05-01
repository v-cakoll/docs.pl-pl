---
title: IMetaDataEmit::SaveToMemory — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc840df9dd0793a7347b7f0d8a05296a09d634c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050067"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="31539-102">IMetaDataEmit::SaveToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="31539-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="31539-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="31539-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31539-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31539-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31539-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="31539-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="31539-106">[out] Adres, od którego należy rozpocząć pisanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="31539-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="31539-107">[in] Rozmiar w bajtach, ilość przydzielonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="31539-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31539-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="31539-108">Requirements</span></span>  
 <span data-ttu-id="31539-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31539-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31539-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="31539-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="31539-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="31539-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="31539-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31539-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31539-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31539-113">See also</span></span>

- [<span data-ttu-id="31539-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="31539-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="31539-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="31539-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
