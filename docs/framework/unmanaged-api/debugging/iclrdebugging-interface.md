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
ms.openlocfilehash: 9a768535c3bf69b5127777de4cee27054943091d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793642"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="48d45-102">ICLRDebugging — Interfejs</span><span class="sxs-lookup"><span data-stu-id="48d45-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="48d45-103">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="48d45-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="48d45-104">Metody</span><span class="sxs-lookup"><span data-stu-id="48d45-104">Methods</span></span>  
  
|<span data-ttu-id="48d45-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="48d45-105">Method</span></span>|<span data-ttu-id="48d45-106">Opis</span><span class="sxs-lookup"><span data-stu-id="48d45-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="48d45-107">OpenVirtualProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="48d45-107">OpenVirtualProcess Method</span></span>](iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="48d45-108">Pobiera interfejs "ICorDebugProcess", który odnosi się do modułu środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="48d45-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="48d45-109">CanUnloadNow, metoda</span><span class="sxs-lookup"><span data-stu-id="48d45-109">CanUnloadNow Method</span></span>](iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="48d45-110">Określa, czy biblioteka, która została dostarczona przez interfejs [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) , jest nadal używana, czy może zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="48d45-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48d45-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48d45-111">Remarks</span></span>  
 <span data-ttu-id="48d45-112">Wystąpienie interfejsu `ICLRDebugging` można uzyskać przy użyciu funkcji [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) .</span><span class="sxs-lookup"><span data-stu-id="48d45-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d45-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48d45-113">Requirements</span></span>  
 <span data-ttu-id="48d45-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48d45-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48d45-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="48d45-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48d45-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="48d45-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48d45-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d45-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d45-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48d45-118">See also</span></span>

- [<span data-ttu-id="48d45-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="48d45-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="48d45-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="48d45-120">Debugging</span></span>](index.md)
