---
title: IAssemblyCache::CreateAssemblyCacheItem — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 215eb3a508a746230d36fdda3e8ba992287be62c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796829"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="d9161-102">IAssemblyCache::CreateAssemblyCacheItem — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9161-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="d9161-103">Pobiera odwołanie do nowego obiektu [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d9161-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9161-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9161-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9161-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9161-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d9161-106">podczas Flagi zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="d9161-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d9161-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="d9161-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="d9161-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="d9161-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="d9161-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="d9161-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="d9161-110">podczas Zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="d9161-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d9161-111">`pvReserved`musi być odwołaniem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="d9161-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="d9161-112">określoną Zwrócony `IAssemblyCacheItem` wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="d9161-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d9161-113">[w, opcjonalnie] Niekanoniczne, pary rozdzielane `name=value` przecinkami.</span><span class="sxs-lookup"><span data-stu-id="d9161-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9161-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9161-114">Requirements</span></span>  
 <span data-ttu-id="d9161-115">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9161-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9161-116">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d9161-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d9161-117">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9161-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9161-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9161-118">See also</span></span>

- [<span data-ttu-id="d9161-119">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9161-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="d9161-120">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9161-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
