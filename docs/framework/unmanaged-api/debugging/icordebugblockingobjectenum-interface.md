---
title: ICorDebugBlockingObjectEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f22d9d86e2b943a8825e1ec271a401b03f73fb6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="77863-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="77863-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="77863-103">Udostępnia moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="77863-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="77863-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="77863-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="77863-105">Metody</span><span class="sxs-lookup"><span data-stu-id="77863-105">Methods</span></span>  
  
|<span data-ttu-id="77863-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="77863-106">Method</span></span>|<span data-ttu-id="77863-107">Opis</span><span class="sxs-lookup"><span data-stu-id="77863-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="77863-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="77863-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="77863-109">Wylicza listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="77863-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77863-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77863-110">Remarks</span></span>  
 <span data-ttu-id="77863-111">Każdy `CorDebugBlockingObject` struktury reprezentuje obiekt, który blokuje wątku.</span><span class="sxs-lookup"><span data-stu-id="77863-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77863-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="77863-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77863-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77863-113">Requirements</span></span>  
 <span data-ttu-id="77863-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77863-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77863-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77863-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77863-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77863-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77863-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77863-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77863-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77863-118">See Also</span></span>  
 [<span data-ttu-id="77863-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="77863-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="77863-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="77863-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
