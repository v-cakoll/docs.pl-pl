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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 651659a48ba9950cdd837889c4491c66fe40b507
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202966"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="b8b69-102">IMetaDataEmit::SetModuleProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="b8b69-102">IMetaDataEmit::SetModuleProps Method</span></span>
<span data-ttu-id="b8b69-103">Aktualizuje odwołania do modułu zdefiniowane przez wcześniejsze wywołanie [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="b8b69-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b8b69-104">Syntax</span></span>  
  
```  
HRESULT SetModuleProps (   
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8b69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b8b69-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="b8b69-106">[in] Nazwa modułu w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="b8b69-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="b8b69-107">Jest to tylko nazwę pliku i nie pełną nazwę ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b8b69-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8b69-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8b69-108">Requirements</span></span>  
 <span data-ttu-id="b8b69-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8b69-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8b69-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b8b69-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8b69-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8b69-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b8b69-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b8b69-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8b69-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8b69-113">See also</span></span>

- [<span data-ttu-id="b8b69-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b8b69-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b8b69-115">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b8b69-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
