---
title: ICorDebugThread2::GetVolatileOSThreadID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetVolatileOSThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetVolatileOSThreadID
helpviewer_keywords:
- GetVolatileOSThreadID method [.NET Framework debugging]
- ICorDebugThread2::GetVolatileOSThreadID method [.NET Framework debugging]
ms.assetid: f0922545-c2cf-40c8-9ef6-ca033563e682
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9bf96371798b38bc392bc6bbd8f6fe8f97c7969
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501971"
---
# <a name="icordebugthread2getvolatileosthreadid-method"></a><span data-ttu-id="e9bd6-102">ICorDebugThread2::GetVolatileOSThreadID — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9bd6-102">ICorDebugThread2::GetVolatileOSThreadID Method</span></span>
<span data-ttu-id="e9bd6-103">Pobiera identyfikator wątku systemu operacyjnego dla tego icordebugthread2 —.</span><span class="sxs-lookup"><span data-stu-id="e9bd6-103">Gets the operating system thread identifier for this ICorDebugThread2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9bd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9bd6-104">Syntax</span></span>  
  
```  
HRESULT GetVolatileOSThreadID (  
    [out] DWORD    *pdwTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9bd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9bd6-105">Parameters</span></span>  
 `pdwTid`  
 <span data-ttu-id="e9bd6-106">[out] Identyfikator wątku systemu operacyjnego dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="e9bd6-106">[out] The operating system thread identifier for this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9bd6-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9bd6-107">Requirements</span></span>  
 <span data-ttu-id="e9bd6-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9bd6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9bd6-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9bd6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9bd6-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9bd6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9bd6-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9bd6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
