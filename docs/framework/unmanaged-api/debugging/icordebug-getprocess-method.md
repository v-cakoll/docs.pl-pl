---
title: ICorDebug::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc095b2c9f546e8b75d4330024c8c593f7ada8b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="491a8-102">ICorDebug::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="491a8-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="491a8-103">Pobiera wskaźnik do wystąpienia "ICorDebugProcess" dla określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="491a8-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="491a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="491a8-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="491a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="491a8-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="491a8-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="491a8-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="491a8-107">[out] Wskaźnik do adresu `ICorDebugProcess` wystąpień określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="491a8-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491a8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="491a8-108">Requirements</span></span>  
 <span data-ttu-id="491a8-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="491a8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491a8-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="491a8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="491a8-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="491a8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="491a8-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491a8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491a8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="491a8-113">See Also</span></span>  
 [<span data-ttu-id="491a8-114">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="491a8-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
