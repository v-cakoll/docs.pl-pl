---
title: "ICLRDebugging — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebugging
helpviewer_keywords: ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3e061b95faafeec3c3d233ab54f128a23c3264
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="1b9cf-102">ICLRDebugging — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1b9cf-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="1b9cf-103">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b9cf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1b9cf-104">Methods</span></span>  
  
|<span data-ttu-id="1b9cf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1b9cf-105">Method</span></span>|<span data-ttu-id="1b9cf-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1b9cf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b9cf-107">OpenVirtualProcess — metoda</span><span class="sxs-lookup"><span data-stu-id="1b9cf-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="1b9cf-108">Pobiera interfejs "ICorDebugProcess", który odpowiada wspólny języka wspólnego (CLR) moduł załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="1b9cf-109">CanUnloadNow — metoda</span><span class="sxs-lookup"><span data-stu-id="1b9cf-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="1b9cf-110">Określa, czy biblioteki, który został dostarczony przez [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu jest nadal używane lub może zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b9cf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b9cf-111">Remarks</span></span>  
 <span data-ttu-id="1b9cf-112">Można uzyskać wystąpienia `ICLRDebugging` interfejsu za pomocą [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="1b9cf-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9cf-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b9cf-113">Requirements</span></span>  
 <span data-ttu-id="1b9cf-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b9cf-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9cf-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b9cf-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b9cf-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b9cf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b9cf-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b9cf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9cf-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b9cf-118">See Also</span></span>  
 [<span data-ttu-id="1b9cf-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="1b9cf-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1b9cf-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1b9cf-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
