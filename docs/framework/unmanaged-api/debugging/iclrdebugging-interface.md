---
title: ICLRDebugging — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
ms.openlocfilehash: 6506b11d97490f796486729dbeb612e47762b60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111437"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="4d3e1-102">ICLRDebugging — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4d3e1-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="4d3e1-103">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="4d3e1-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d3e1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d3e1-104">Methods</span></span>  
  
|<span data-ttu-id="4d3e1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d3e1-105">Method</span></span>|<span data-ttu-id="4d3e1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4d3e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d3e1-107">OpenVirtualProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="4d3e1-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="4d3e1-108">Pobiera interfejs "ICorDebugProcess", który odnosi się do modułu środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="4d3e1-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="4d3e1-109">CanUnloadNow, metoda</span><span class="sxs-lookup"><span data-stu-id="4d3e1-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="4d3e1-110">Określa, czy biblioteka, która została dostarczona przez interfejs [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) , jest nadal używana, czy może zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="4d3e1-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d3e1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d3e1-111">Remarks</span></span>  
 <span data-ttu-id="4d3e1-112">Wystąpienie interfejsu `ICLRDebugging` można uzyskać przy użyciu funkcji [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="4d3e1-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d3e1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d3e1-113">Requirements</span></span>  
 <span data-ttu-id="4d3e1-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d3e1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d3e1-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4d3e1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d3e1-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d3e1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d3e1-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d3e1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3e1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d3e1-118">See also</span></span>

- [<span data-ttu-id="4d3e1-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4d3e1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4d3e1-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4d3e1-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
