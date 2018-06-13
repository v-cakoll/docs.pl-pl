---
title: ICorDebugUnmanagedCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback
helpviewer_keywords:
- ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b55b27d45ef3efea10215c8a4163b5981f9d145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422864"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="52b4c-102">ICorDebugUnmanagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="52b4c-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="52b4c-103">Zapewnia powiadomienie natywnego zdarzeń, które nie są bezpośrednio związane z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="52b4c-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52b4c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="52b4c-104">Methods</span></span>  
  
|<span data-ttu-id="52b4c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="52b4c-105">Method</span></span>|<span data-ttu-id="52b4c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="52b4c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52b4c-107">DebugEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="52b4c-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="52b4c-108">Powiadamia debugera natywnego zdarzenia uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="52b4c-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52b4c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52b4c-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52b4c-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="52b4c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b4c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52b4c-111">Requirements</span></span>  
 <span data-ttu-id="52b4c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52b4c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b4c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52b4c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52b4c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52b4c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52b4c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b4c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b4c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52b4c-116">See Also</span></span>  
 [<span data-ttu-id="52b4c-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="52b4c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
