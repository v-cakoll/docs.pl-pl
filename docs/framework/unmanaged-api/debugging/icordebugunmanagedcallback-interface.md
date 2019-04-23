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
ms.openlocfilehash: 60a1546068ae6a8c8be1c0af1ef3c7d770c23d70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128683"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="89a3d-102">ICorDebugUnmanagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="89a3d-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="89a3d-103">Zapewnia powiadomienie macierzystych zdarzeń, które nie są bezpośrednio związane z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="89a3d-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89a3d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89a3d-104">Methods</span></span>  
  
|<span data-ttu-id="89a3d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89a3d-105">Method</span></span>|<span data-ttu-id="89a3d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="89a3d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89a3d-107">DebugEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="89a3d-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="89a3d-108">Powiadamia debuger natywny zdarzenia uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="89a3d-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89a3d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89a3d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89a3d-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="89a3d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89a3d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89a3d-111">Requirements</span></span>  
 <span data-ttu-id="89a3d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89a3d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89a3d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89a3d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89a3d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89a3d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89a3d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89a3d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a3d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89a3d-116">See also</span></span>

- [<span data-ttu-id="89a3d-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="89a3d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
