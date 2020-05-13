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
ms.openlocfilehash: ce3ca4745727a1738fdc1a526480d70ffc55ccf8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209906"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="dad1a-102">ICorDebugInternalFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dad1a-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="dad1a-103">Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do obiektów ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="dad1a-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dad1a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dad1a-104">Methods</span></span>  
  
|<span data-ttu-id="dad1a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dad1a-105">Method</span></span>|<span data-ttu-id="dad1a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dad1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dad1a-107">GetFrameAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="dad1a-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="dad1a-108">Zwraca adres stosu ramki wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="dad1a-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="dad1a-109">IsCloserToLeaf, metoda</span><span class="sxs-lookup"><span data-stu-id="dad1a-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="dad1a-110">Sprawdza, czy `this` wewnętrzna ramka jest bliżej liścia niż określony obiekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="dad1a-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dad1a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dad1a-111">Remarks</span></span>  
 <span data-ttu-id="dad1a-112">Ten interfejs rozszerza interfejs ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="dad1a-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dad1a-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="dad1a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad1a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dad1a-114">Requirements</span></span>  
 <span data-ttu-id="dad1a-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dad1a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad1a-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dad1a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dad1a-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dad1a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dad1a-118">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad1a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad1a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dad1a-119">See also</span></span>

- [<span data-ttu-id="dad1a-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="dad1a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="dad1a-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="dad1a-121">Debugging</span></span>](index.md)
