---
title: IMetaDataEmit::Save — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: 76f18336808e6832b2ded94349efd7948f23a1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175697"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="fc0d3-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc0d3-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="fc0d3-103">Zapisuje wszystkie metadane w bieżącym zakresie do pliku pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="fc0d3-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc0d3-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (
    [in]  LPCWSTR     szFile,
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc0d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc0d3-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="fc0d3-106">[w] Nazwa pliku do zapisania.</span><span class="sxs-lookup"><span data-stu-id="fc0d3-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="fc0d3-107">Jeśli ta wartość ma wartość null, kopia w pamięci zostanie zapisana w ostatniej lokalizacji, która została użyta.</span><span class="sxs-lookup"><span data-stu-id="fc0d3-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="fc0d3-108">[w] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="fc0d3-108">[in] Reserved.</span></span> <span data-ttu-id="fc0d3-109">Musi być zero.</span><span class="sxs-lookup"><span data-stu-id="fc0d3-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0d3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc0d3-110">Requirements</span></span>  
 <span data-ttu-id="fc0d3-111">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc0d3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc0d3-112">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc0d3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc0d3-113">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc0d3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc0d3-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc0d3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0d3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc0d3-115">See also</span></span>

- [<span data-ttu-id="fc0d3-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fc0d3-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fc0d3-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc0d3-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
