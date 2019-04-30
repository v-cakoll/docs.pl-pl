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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3757eee4c013ccf4f0f6d21ef64a92a5ffd70f19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697506"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="12d39-102">IAssemblyCacheItem::Commit — Metoda</span><span class="sxs-lookup"><span data-stu-id="12d39-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="12d39-103">Zatwierdza odwołanie do zestawu pamięci podręcznej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="12d39-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d39-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12d39-104">Syntax</span></span>  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12d39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="12d39-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="12d39-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="12d39-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="12d39-107">[out, opcjonalny] Wartość, która wskazuje wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="12d39-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12d39-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12d39-108">Requirements</span></span>  
 <span data-ttu-id="12d39-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12d39-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12d39-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="12d39-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="12d39-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12d39-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d39-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12d39-112">See also</span></span>

- [<span data-ttu-id="12d39-113">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="12d39-113">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
