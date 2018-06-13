---
title: ICorDebugMDA::GetOSThreadId — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20833624b4b853a1a56964e11a25f446c6b39053
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414716"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="e34bb-102">ICorDebugMDA::GetOSThreadId — Metoda</span><span class="sxs-lookup"><span data-stu-id="e34bb-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="e34bb-103">Pobiera identyfikator wątku systemu operacyjnego (OS), na którym zarządzany Asystent debugowania (MDA) reprezentowany przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="e34bb-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e34bb-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e34bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e34bb-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="e34bb-106">[out] Wskaźnik do identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e34bb-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e34bb-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e34bb-107">Remarks</span></span>  
 <span data-ttu-id="e34bb-108">Wątek systemu operacyjnego umożliwia zamiast ICorDebugThread w sytuacjach, w których MDA jest uruchamiany na wątku natywnego lub zarządzanego wątku, który nie ma jeszcze wprowadzone kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e34bb-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e34bb-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e34bb-109">Requirements</span></span>  
 <span data-ttu-id="e34bb-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e34bb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e34bb-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e34bb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e34bb-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e34bb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e34bb-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e34bb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34bb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e34bb-114">See Also</span></span>  
 [<span data-ttu-id="e34bb-115">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="e34bb-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="e34bb-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="e34bb-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
