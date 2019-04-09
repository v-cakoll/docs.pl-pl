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
ms.openlocfilehash: 49e45085b0fbca10e490f11ce588f68aa8237b46
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59139077"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="64d55-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="64d55-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="64d55-103">Zapisuje wszystkie metadane w bieżącym zakresie pliku pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="64d55-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64d55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64d55-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64d55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64d55-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="64d55-106">[in] Nazwa pliku, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="64d55-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="64d55-107">Jeśli ta wartość jest równa null, kopię znajdującą się w pamięci zostaną zapisane do ostatnich lokalizacji, który został użyty.</span><span class="sxs-lookup"><span data-stu-id="64d55-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="64d55-108">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="64d55-108">[in] Reserved.</span></span> <span data-ttu-id="64d55-109">Musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="64d55-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64d55-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64d55-110">Requirements</span></span>  
 <span data-ttu-id="64d55-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64d55-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64d55-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="64d55-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="64d55-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="64d55-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="64d55-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="64d55-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="64d55-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64d55-115">See also</span></span>

- [<span data-ttu-id="64d55-116">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64d55-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="64d55-117">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="64d55-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
