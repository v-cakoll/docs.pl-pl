---
title: "IAssemblyCache::CreateAssemblyCacheItem — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 65431425afb6a666679d29f9c1bbc9691caa0afb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="eb18f-102">IAssemblyCache::CreateAssemblyCacheItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="eb18f-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="eb18f-103">Pobiera odwołanie do nowego [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="eb18f-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb18f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb18f-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb18f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb18f-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="eb18f-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="eb18f-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="eb18f-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="eb18f-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="eb18f-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="eb18f-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="eb18f-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="eb18f-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="eb18f-110">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="eb18f-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="eb18f-111">`pvReserved`musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="eb18f-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="eb18f-112">[out] Zwrócona `IAssemblyCacheItem` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="eb18f-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="eb18f-113">[w, opcjonalnie] Uncanonicalized, rozdzielone przecinkami `name=value` pary.</span><span class="sxs-lookup"><span data-stu-id="eb18f-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb18f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb18f-114">Requirements</span></span>  
 <span data-ttu-id="eb18f-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb18f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb18f-116">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="eb18f-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="eb18f-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb18f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb18f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb18f-118">See Also</span></span>  
 [<span data-ttu-id="eb18f-119">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb18f-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="eb18f-120">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="eb18f-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
