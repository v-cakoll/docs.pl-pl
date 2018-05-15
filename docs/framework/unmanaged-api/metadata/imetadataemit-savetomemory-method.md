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
ms.openlocfilehash: b680e807554a60711e61729680e9c9fcf1c8fdaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="c859a-102">IMetaDataEmit::SaveToMemory — Metoda</span><span class="sxs-lookup"><span data-stu-id="c859a-102">IMetaDataEmit::SaveToMemory Method</span></span>
<span data-ttu-id="c859a-103">Zapisuje wszystkie metadane w bieżącym zakresie do określonego obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="c859a-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c859a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c859a-104">Syntax</span></span>  
  
```  
HRESULT SaveToMemory (   
    [out]  void        *pbData,   
    [in]   ULONG       cbData   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c859a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c859a-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="c859a-106">[out] Adres, od którego należy zacząć zapisywania metadanych.</span><span class="sxs-lookup"><span data-stu-id="c859a-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="c859a-107">[in] Rozmiar w bajtach alokacji pamięci.</span><span class="sxs-lookup"><span data-stu-id="c859a-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c859a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c859a-108">Requirements</span></span>  
 <span data-ttu-id="c859a-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c859a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c859a-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c859a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c859a-111">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c859a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c859a-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c859a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c859a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c859a-113">See Also</span></span>  
 [<span data-ttu-id="c859a-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c859a-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c859a-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c859a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
