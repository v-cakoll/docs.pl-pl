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
ms.openlocfilehash: ccf82531eb1f78bcfc6762d10d53ffee59f30ad8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003961"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="5db39-102">IMetaDataEmit::SaveToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="5db39-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="5db39-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="5db39-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5db39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5db39-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5db39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5db39-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="5db39-106">określoną Adres, pod którym należy zacząć pisać metadane.</span><span class="sxs-lookup"><span data-stu-id="5db39-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="5db39-107">podczas Rozmiar przydzieloną pamięci (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="5db39-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5db39-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5db39-108">Requirements</span></span>  
 <span data-ttu-id="5db39-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5db39-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5db39-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5db39-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5db39-111">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5db39-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5db39-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5db39-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db39-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5db39-113">See also</span></span>

- [<span data-ttu-id="5db39-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5db39-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5db39-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5db39-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
