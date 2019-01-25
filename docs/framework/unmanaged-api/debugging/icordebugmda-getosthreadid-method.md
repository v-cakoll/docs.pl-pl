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
ms.openlocfilehash: e67e3bc3477e078a4f1d963cdd768676503dc953
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607666"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="c9a85-102">ICorDebugMDA::GetOSThreadId — Metoda</span><span class="sxs-lookup"><span data-stu-id="c9a85-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="c9a85-103">Pobiera identyfikator wątku systemu operacyjnego (OS), na którym zarządzanego Asystenta debugowania (MDA) jest reprezentowane przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="c9a85-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9a85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9a85-104">Syntax</span></span>  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9a85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9a85-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="c9a85-106">[out] Wskaźnik do identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c9a85-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9a85-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9a85-107">Remarks</span></span>  
 <span data-ttu-id="c9a85-108">Wątek systemu operacyjnego umożliwia zamiast ICorDebugThread w sytuacjach, w których MDA jest uruchamiany na wątku natywnej lub z wątków zarządzanych, które jeszcze nie wprowadzono kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="c9a85-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9a85-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c9a85-109">Requirements</span></span>  
 <span data-ttu-id="c9a85-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9a85-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9a85-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9a85-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9a85-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9a85-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9a85-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9a85-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a85-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9a85-114">See also</span></span>
- [<span data-ttu-id="c9a85-115">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="c9a85-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="c9a85-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="c9a85-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
