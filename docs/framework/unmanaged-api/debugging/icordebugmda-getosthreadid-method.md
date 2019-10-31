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
ms.openlocfilehash: e9846234f8217b822860c2400a54a91a651a0a56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129820"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="55055-102">ICorDebugMDA::GetOSThreadId — Metoda</span><span class="sxs-lookup"><span data-stu-id="55055-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="55055-103">Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywany Asystent debugowania zarządzanego (MDA) reprezentowany przez [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="55055-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55055-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55055-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55055-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55055-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="55055-106">określoną Wskaźnik do identyfikatora wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="55055-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55055-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55055-107">Remarks</span></span>  
 <span data-ttu-id="55055-108">Wątek systemu operacyjnego jest używany zamiast ICorDebugThread, aby umożliwić sytuacje, w których zdarzenie MDA jest wywoływane w wątku macierzystym lub w zarządzanym wątku, które nie podano jeszcze kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="55055-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55055-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55055-109">Requirements</span></span>  
 <span data-ttu-id="55055-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55055-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55055-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55055-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55055-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="55055-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55055-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55055-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55055-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55055-114">See also</span></span>

- [<span data-ttu-id="55055-115">ICorDebugMDA, interfejs</span><span class="sxs-lookup"><span data-stu-id="55055-115">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [<span data-ttu-id="55055-116">Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania</span><span class="sxs-lookup"><span data-stu-id="55055-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
