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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993762"
---
# <a name="icordebugunmanagedcallback-interface"></a><span data-ttu-id="da066-102">ICorDebugUnmanagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="da066-102">ICorDebugUnmanagedCallback Interface</span></span>
<span data-ttu-id="da066-103">Zapewnia powiadomienie macierzystych zdarzeń, które nie są bezpośrednio związane z środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="da066-103">Provides notification of native events that are not directly related to the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da066-104">Metody</span><span class="sxs-lookup"><span data-stu-id="da066-104">Methods</span></span>  
  
|<span data-ttu-id="da066-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="da066-105">Method</span></span>|<span data-ttu-id="da066-106">Opis</span><span class="sxs-lookup"><span data-stu-id="da066-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da066-107">DebugEvent, metoda</span><span class="sxs-lookup"><span data-stu-id="da066-107">DebugEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md)|<span data-ttu-id="da066-108">Powiadamia debuger natywny zdarzenia uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="da066-108">Notifies the debugger that a native event has been fired.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da066-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da066-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da066-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="da066-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da066-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da066-111">Requirements</span></span>  
 <span data-ttu-id="da066-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da066-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da066-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da066-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da066-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da066-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da066-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da066-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da066-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da066-116">See also</span></span>

- [<span data-ttu-id="da066-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="da066-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
