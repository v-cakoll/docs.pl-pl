---
title: "ICorDebugUnmanagedCallback — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback
helpviewer_keywords: ICorDebugUnmanagedCallback interface [.NET Framework debugging]
ms.assetid: bc71cbca-7d73-40e5-84dd-2109fade3c2a
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aa104bee5171b3b28731cf18a4d26e32f49169ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="7e6e1-102">ICorDebugUnmanagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7e6e1-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="7e6e1-103">Zapewnia powiadomienie natywnego zdarzeń, które nie są bezpośrednio związane z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7e6e1-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e6e1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7e6e1-104">Methods</span></span>  
  
|<span data-ttu-id="7e6e1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7e6e1-105">Method</span></span>|<span data-ttu-id="7e6e1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7e6e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e6e1-107">DebugEvent — metoda</span><span class="sxs-lookup"><span data-stu-id="7e6e1-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="7e6e1-108">Powiadamia debugera natywnego zdarzenia uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="7e6e1-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e6e1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7e6e1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e6e1-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="7e6e1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e6e1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7e6e1-111">Requirements</span></span>  
 <span data-ttu-id="7e6e1-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e6e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e6e1-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e6e1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e6e1-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e6e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e6e1-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e6e1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e6e1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e6e1-116">See Also</span></span>  
 [<span data-ttu-id="7e6e1-117">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="7e6e1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
