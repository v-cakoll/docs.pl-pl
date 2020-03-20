---
title: IAssemblyCacheItem::Commit — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCacheItem.Commit
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type:
- apiref
ms.openlocfilehash: f840438e175790a2b4c97302963b910f98dffb7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176568"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="92e60-102">IAssemblyCacheItem::Commit — Metoda</span><span class="sxs-lookup"><span data-stu-id="92e60-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="92e60-103">Zatwierdza odwołanie do zestawu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="92e60-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92e60-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92e60-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92e60-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92e60-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="92e60-106">[w] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="92e60-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="92e60-107">[out, opcjonalnie] Wartość, która wskazuje wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="92e60-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92e60-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92e60-108">Requirements</span></span>  
 <span data-ttu-id="92e60-109">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92e60-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92e60-110">**Nagłówek:** Fuzja.h</span><span class="sxs-lookup"><span data-stu-id="92e60-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="92e60-111">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92e60-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e60-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92e60-112">See also</span></span>

- [<span data-ttu-id="92e60-113">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="92e60-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
