---
title: "CreateAssemblyCache — Funkcja"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5e730ea9f83a40d92cb6a865fcdd87ebf523fe7c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="createassemblycache-function"></a><span data-ttu-id="32407-102">CreateAssemblyCache — Funkcja</span><span class="sxs-lookup"><span data-stu-id="32407-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="32407-103">Pobiera wskaźnik do nowego [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) wystąpienie reprezentującego globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="32407-103">Gets a pointer to a new [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32407-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32407-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="32407-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32407-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="32407-106">[out] Zwrócona `IAssemblyCache` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="32407-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="32407-107">[in] Zarezerwowane dla przyszłego rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="32407-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="32407-108">`dwReserved`musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="32407-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32407-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32407-109">Requirements</span></span>  
 <span data-ttu-id="32407-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32407-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32407-111">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="32407-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="32407-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32407-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="32407-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32407-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32407-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32407-114">See Also</span></span>  
 [<span data-ttu-id="32407-115">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="32407-115">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="32407-116">Łączenie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="32407-116">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="32407-117">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="32407-117">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
