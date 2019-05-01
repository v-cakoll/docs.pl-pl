---
title: ICorDebugChain::GetThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ab2b584b4a3e9bef17110f3084dc93efb2e5167
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989368"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="b3d4c-102">ICorDebugChain::GetThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3d4c-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="b3d4c-103">Pobiera wątku fizycznym, ten łańcuch wywołań jest częścią.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d4c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3d4c-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3d4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3d4c-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="b3d4c-106">[out] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku fizycznym tego łańcucha wywołań jest częścią.</span><span class="sxs-lookup"><span data-stu-id="b3d4c-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3d4c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3d4c-107">Requirements</span></span>  
 <span data-ttu-id="b3d4c-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3d4c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3d4c-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3d4c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3d4c-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3d4c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3d4c-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3d4c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
