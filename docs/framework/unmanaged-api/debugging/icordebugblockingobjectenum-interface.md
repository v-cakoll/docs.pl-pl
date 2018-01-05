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
ms.workload: dotnet
ms.openlocfilehash: d35d4ee2ce3c1b7b0f54d78dba8b8639c522d509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="bf7b2-102">ICorDebugBlockingObjectEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf7b2-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="bf7b2-103">Udostępnia moduł wyliczający listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="bf7b2-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf7b2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bf7b2-105">Methods</span></span>  
  
|<span data-ttu-id="bf7b2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf7b2-106">Method</span></span>|<span data-ttu-id="bf7b2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf7b2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf7b2-108">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="bf7b2-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="bf7b2-109">Wylicza listę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf7b2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf7b2-110">Remarks</span></span>  
 <span data-ttu-id="bf7b2-111">Każdy `CorDebugBlockingObject` struktury reprezentuje obiekt, który blokuje wątku.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf7b2-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="bf7b2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf7b2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf7b2-113">Requirements</span></span>  
 <span data-ttu-id="bf7b2-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf7b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf7b2-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf7b2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf7b2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf7b2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf7b2-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf7b2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf7b2-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf7b2-118">See Also</span></span>  
 [<span data-ttu-id="bf7b2-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bf7b2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bf7b2-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bf7b2-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
