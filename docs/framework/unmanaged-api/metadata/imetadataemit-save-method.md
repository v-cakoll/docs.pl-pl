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
ms.openlocfilehash: 1a2be03e82d5be9bae64d7169709d16c40b66e37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511883"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="9ccfe-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="9ccfe-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="9ccfe-103">Zapisuje wszystkie metadane w bieżącym zakresie pliku pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="9ccfe-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ccfe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ccfe-104">Syntax</span></span>  
  
```  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ccfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ccfe-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="9ccfe-106">[in] Nazwa pliku, aby zapisać.</span><span class="sxs-lookup"><span data-stu-id="9ccfe-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="9ccfe-107">Jeśli ta wartość jest równa null, kopię znajdującą się w pamięci zostaną zapisane do ostatnich lokalizacji, który został użyty.</span><span class="sxs-lookup"><span data-stu-id="9ccfe-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="9ccfe-108">[in] Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="9ccfe-108">[in] Reserved.</span></span> <span data-ttu-id="9ccfe-109">Musi mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="9ccfe-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ccfe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ccfe-110">Requirements</span></span>  
 <span data-ttu-id="9ccfe-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ccfe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ccfe-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9ccfe-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ccfe-113">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ccfe-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ccfe-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ccfe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccfe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ccfe-115">See also</span></span>
- [<span data-ttu-id="9ccfe-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ccfe-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9ccfe-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ccfe-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
