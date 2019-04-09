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
ms.openlocfilehash: 51d29fed3d53611daa0042251ce09638399f7ed5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195803"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="9a7cd-102">ICorDebugMDA::GetOSThreadId — Metoda</span><span class="sxs-lookup"><span data-stu-id="9a7cd-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="9a7cd-103">Pobiera identyfikator wątku systemu operacyjnego (OS), na którym zarządzanego Asystenta debugowania (MDA) jest reprezentowane przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="9a7cd-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a7cd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a7cd-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a7cd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a7cd-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="9a7cd-106">[out] Wskaźnik do identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9a7cd-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a7cd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9a7cd-107">Remarks</span></span>  
 <span data-ttu-id="9a7cd-108">Wątek systemu operacyjnego umożliwia zamiast ICorDebugThread w sytuacjach, w których MDA jest uruchamiany na wątku natywnej lub z wątków zarządzanych, które jeszcze nie wprowadzono kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9a7cd-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a7cd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a7cd-109">Requirements</span></span>  
 <span data-ttu-id="9a7cd-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a7cd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a7cd-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a7cd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a7cd-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a7cd-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9a7cd-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9a7cd-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9a7cd-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a7cd-114">See also</span></span>

- [<span data-ttu-id="9a7cd-115">ICorDebugMDA — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9a7cd-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="9a7cd-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="9a7cd-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
