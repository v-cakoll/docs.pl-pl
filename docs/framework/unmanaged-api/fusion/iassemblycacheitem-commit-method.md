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
ms.openlocfilehash: 380181d8e309ba4b51d49aae9159f0bbf7e0250f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796716"
---
# <a name="iassemblycacheitemcommit-method"></a><span data-ttu-id="703d4-102">IAssemblyCacheItem::Commit — Metoda</span><span class="sxs-lookup"><span data-stu-id="703d4-102">IAssemblyCacheItem::Commit Method</span></span>
<span data-ttu-id="703d4-103">Zatwierdza odwołanie do pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="703d4-103">Commits the cached assembly reference to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="703d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="703d4-104">Syntax</span></span>  
  
```cpp  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="703d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="703d4-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="703d4-106">podczas Flagi zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="703d4-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="703d4-107">[out, opcjonalne] Wartość, która wskazuje wynik operacji.</span><span class="sxs-lookup"><span data-stu-id="703d4-107">[out, optional] A value that indicates the result of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="703d4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="703d4-108">Requirements</span></span>  
 <span data-ttu-id="703d4-109">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="703d4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="703d4-110">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="703d4-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="703d4-111">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="703d4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="703d4-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="703d4-112">See also</span></span>

- [<span data-ttu-id="703d4-113">IAssemblyCacheItem, interfejs</span><span class="sxs-lookup"><span data-stu-id="703d4-113">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
