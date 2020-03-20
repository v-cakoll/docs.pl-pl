---
title: IMetaDataEmit::SetModuleProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 69c3ee366dbb8505e0df744037c480da996bb836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175619"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="ba6ba-102">IMetaDataEmit::SetModuleProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ba6ba-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="ba6ba-103">Aktualizuje odwołania do modułu zdefiniowanego przez wcześniejsze wywołanie [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="ba6ba-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba6ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba6ba-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba6ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ba6ba-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="ba6ba-106">[w] Nazwa modułu w Unicode.</span><span class="sxs-lookup"><span data-stu-id="ba6ba-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="ba6ba-107">Jest to tylko nazwa pliku, a nie pełna nazwa ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ba6ba-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba6ba-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba6ba-108">Requirements</span></span>  
 <span data-ttu-id="ba6ba-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba6ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba6ba-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba6ba-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba6ba-111">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba6ba-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba6ba-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba6ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6ba-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba6ba-113">See also</span></span>

- [<span data-ttu-id="ba6ba-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ba6ba-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ba6ba-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba6ba-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
