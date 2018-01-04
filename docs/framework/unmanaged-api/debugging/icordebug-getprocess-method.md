---
title: "ICorDebug::GetProcess — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3acdcb15f22c130601394ee1bb259207e5e3df23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="a08df-102">ICorDebug::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="a08df-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="a08df-103">Pobiera wskaźnik do wystąpienia "ICorDebugProcess" dla określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a08df-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a08df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a08df-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a08df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a08df-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="a08df-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="a08df-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a08df-107">[out] Wskaźnik do adresu `ICorDebugProcess` wystąpień określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="a08df-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a08df-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a08df-108">Requirements</span></span>  
 <span data-ttu-id="a08df-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a08df-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a08df-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a08df-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a08df-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a08df-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a08df-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a08df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08df-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a08df-113">See Also</span></span>  
 [<span data-ttu-id="a08df-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a08df-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
