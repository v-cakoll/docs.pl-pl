---
title: "ICorDebugInternalFrame2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d87303fbe95804b458a42ed43b65f29233814977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="0023c-102">ICorDebugInternalFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0023c-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="0023c-103">Zawiera informacje dotyczące wewnętrznego ramki, w tym adresu stosu i pozycji w odniesieniu do obiektów ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0023c-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0023c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0023c-104">Methods</span></span>  
  
|<span data-ttu-id="0023c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0023c-105">Method</span></span>|<span data-ttu-id="0023c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0023c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0023c-107">GetFrameAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="0023c-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="0023c-108">Zwraca adres stosu wewnętrznego ramki.</span><span class="sxs-lookup"><span data-stu-id="0023c-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="0023c-109">IsCloserToLeaf, metoda</span><span class="sxs-lookup"><span data-stu-id="0023c-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="0023c-110">Sprawdza, czy `this` wewnętrzny ramki jest bliżej niż określony obiekt ICorDebugFrame liścia.</span><span class="sxs-lookup"><span data-stu-id="0023c-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0023c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0023c-111">Remarks</span></span>  
 <span data-ttu-id="0023c-112">Ten interfejs umożliwia rozbudowywanie interfejsu ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="0023c-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0023c-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="0023c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0023c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0023c-114">Requirements</span></span>  
 <span data-ttu-id="0023c-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0023c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0023c-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0023c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0023c-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0023c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0023c-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0023c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0023c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0023c-119">See Also</span></span>  
 [<span data-ttu-id="0023c-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0023c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0023c-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0023c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
