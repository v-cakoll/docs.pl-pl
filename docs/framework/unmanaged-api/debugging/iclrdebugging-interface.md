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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6edee34c8560c989040475fee4a35c6bd2ddb3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697995"
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="a457c-102">ICLRDebugging — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a457c-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="a457c-103">Zapewnia metody obsługujące ładowanie i wyładowanie modułów do debugowania.</span><span class="sxs-lookup"><span data-stu-id="a457c-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a457c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a457c-104">Methods</span></span>  
  
|<span data-ttu-id="a457c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a457c-105">Method</span></span>|<span data-ttu-id="a457c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a457c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a457c-107">OpenVirtualProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="a457c-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="a457c-108">Pobiera interfejs "ICorDebugProcess", który odnosi się do wspólnego języka wspólnego (CLR) moduł załadowany w procesie.</span><span class="sxs-lookup"><span data-stu-id="a457c-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="a457c-109">CanUnloadNow, metoda</span><span class="sxs-lookup"><span data-stu-id="a457c-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="a457c-110">Określa, czy biblioteka, który został dostarczony przez [iclrdebugginglibraryprovider —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interfejsu jest nadal w użyciu lub może być zwolniony.</span><span class="sxs-lookup"><span data-stu-id="a457c-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a457c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a457c-111">Remarks</span></span>  
 <span data-ttu-id="a457c-112">Możesz uzyskać wystąpienie `ICLRDebugging` interfejs, za pomocą [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="a457c-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a457c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a457c-113">Requirements</span></span>  
 <span data-ttu-id="a457c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a457c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a457c-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a457c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a457c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a457c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a457c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a457c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a457c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a457c-118">See also</span></span>

- [<span data-ttu-id="a457c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a457c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a457c-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="a457c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
