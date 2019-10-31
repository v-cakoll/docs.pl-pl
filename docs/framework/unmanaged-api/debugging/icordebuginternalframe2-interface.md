---
title: ICorDebugInternalFrame2 — Interfejs
ms.date: 03/30/2017
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
ms.openlocfilehash: 5a451218e0fdc32132a4e79d091ada8355d32fe7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122689"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="b1bb6-102">ICorDebugInternalFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1bb6-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="b1bb6-103">Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do obiektów ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="b1bb6-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1bb6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b1bb6-104">Methods</span></span>  
  
|<span data-ttu-id="b1bb6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1bb6-105">Method</span></span>|<span data-ttu-id="b1bb6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b1bb6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1bb6-107">GetFrameAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="b1bb6-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="b1bb6-108">Zwraca adres stosu ramki wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="b1bb6-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="b1bb6-109">IsCloserToLeaf, metoda</span><span class="sxs-lookup"><span data-stu-id="b1bb6-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="b1bb6-110">Sprawdza, czy `this` wewnętrzna ramka jest bliżej liścia niż określony obiekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="b1bb6-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1bb6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1bb6-111">Remarks</span></span>  
 <span data-ttu-id="b1bb6-112">Ten interfejs rozszerza interfejs ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="b1bb6-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1bb6-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b1bb6-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bb6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1bb6-114">Requirements</span></span>  
 <span data-ttu-id="b1bb6-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bb6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bb6-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1bb6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1bb6-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1bb6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1bb6-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bb6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bb6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1bb6-119">See also</span></span>

- [<span data-ttu-id="b1bb6-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b1bb6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b1bb6-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b1bb6-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
