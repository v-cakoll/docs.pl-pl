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
ms.openlocfilehash: 9e333d71505a055cfe27df2c79a102c939bafc9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788476"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="06150-102">ICorDebugInternalFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06150-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="06150-103">Zawiera informacje o ramkach wewnętrznych, łącznie z adresem stosu i pozycją w odniesieniu do obiektów ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="06150-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06150-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06150-104">Methods</span></span>  
  
|<span data-ttu-id="06150-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06150-105">Method</span></span>|<span data-ttu-id="06150-106">Opis</span><span class="sxs-lookup"><span data-stu-id="06150-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06150-107">GetFrameAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="06150-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="06150-108">Zwraca adres stosu ramki wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="06150-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="06150-109">IsCloserToLeaf, metoda</span><span class="sxs-lookup"><span data-stu-id="06150-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="06150-110">Sprawdza, czy `this` wewnętrzna ramka jest bliżej liścia niż określony obiekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="06150-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06150-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06150-111">Remarks</span></span>  
 <span data-ttu-id="06150-112">Ten interfejs rozszerza interfejs ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="06150-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06150-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="06150-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06150-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06150-114">Requirements</span></span>  
 <span data-ttu-id="06150-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06150-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06150-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="06150-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06150-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06150-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06150-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06150-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06150-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06150-119">See also</span></span>

- [<span data-ttu-id="06150-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="06150-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="06150-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="06150-121">Debugging</span></span>](index.md)
