---
title: "ICorDebugBlockingObjectEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum
helpviewer_keywords: ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b62da4047029881ddffff5faee9f06072407bfc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="7b339-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7b339-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="7b339-103">Udostępnia moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="7b339-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="7b339-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="7b339-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b339-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7b339-105">Methods</span></span>  
  
|<span data-ttu-id="7b339-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7b339-106">Method</span></span>|<span data-ttu-id="7b339-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7b339-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b339-108">Next — metoda</span><span class="sxs-lookup"><span data-stu-id="7b339-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="7b339-109">Wylicza listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="7b339-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b339-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b339-110">Remarks</span></span>  
 <span data-ttu-id="7b339-111">Każdy `CorDebugBlockingObject` struktury reprezentuje obiekt, który blokuje wątku.</span><span class="sxs-lookup"><span data-stu-id="7b339-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b339-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="7b339-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b339-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b339-113">Requirements</span></span>  
 <span data-ttu-id="7b339-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b339-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b339-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b339-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b339-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b339-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b339-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b339-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b339-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b339-118">See Also</span></span>  
 [<span data-ttu-id="7b339-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="7b339-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7b339-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7b339-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
