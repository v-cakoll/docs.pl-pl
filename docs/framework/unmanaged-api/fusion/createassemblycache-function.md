---
title: CreateAssemblyCache — Funkcja
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5869bf22c74a232f20fc49fe81a6a35c9738f1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735032"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="3cf42-102">CreateAssemblyCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="3cf42-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="3cf42-103">Pobiera wskaźnik do nowego [iassemblycache —](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) wystąpienia, która reprezentuje globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="3cf42-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cf42-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3cf42-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3cf42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cf42-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="3cf42-106">[out] Zwrócony `IAssemblyCache` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="3cf42-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="3cf42-107">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="3cf42-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="3cf42-108">`dwReserved` musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="3cf42-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cf42-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3cf42-109">Requirements</span></span>  
 <span data-ttu-id="3cf42-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cf42-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cf42-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="3cf42-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="3cf42-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3cf42-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3cf42-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cf42-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf42-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cf42-114">See also</span></span>
- [<span data-ttu-id="3cf42-115">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="3cf42-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="3cf42-116">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="3cf42-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="3cf42-117">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="3cf42-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
