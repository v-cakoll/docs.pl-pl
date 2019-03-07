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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90ddc540115a60154953ac6e8cb931103a650752
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492418"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="36f36-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="36f36-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="36f36-103">Zapisuje wszystkie metadane w bieżącym zakresie pliku pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="36f36-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36f36-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="36f36-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36f36-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36f36-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="36f36-106">[in] Nazwa pliku, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="36f36-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="36f36-107">Jeśli ta wartość jest równa null, kopię znajdującą się w pamięci zostaną zapisane do ostatnich lokalizacji, który został użyty.</span><span class="sxs-lookup"><span data-stu-id="36f36-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="36f36-108">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="36f36-108">[in] Reserved.</span></span> <span data-ttu-id="36f36-109">Musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="36f36-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36f36-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36f36-110">Requirements</span></span>  
 <span data-ttu-id="36f36-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36f36-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36f36-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="36f36-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36f36-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36f36-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36f36-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36f36-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36f36-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36f36-115">See also</span></span>
- [<span data-ttu-id="36f36-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="36f36-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="36f36-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="36f36-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
