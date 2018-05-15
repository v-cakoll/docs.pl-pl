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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4082c4204b85aba97651419db15ba8eb4c3d54e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="57c7e-102">ICorDebugInternalFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="57c7e-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="57c7e-103">Zawiera informacje dotyczące wewnętrznego ramki, w tym adresu stosu i pozycji w odniesieniu do obiektów ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="57c7e-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57c7e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57c7e-104">Methods</span></span>  
  
|<span data-ttu-id="57c7e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57c7e-105">Method</span></span>|<span data-ttu-id="57c7e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="57c7e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57c7e-107">GetFrameAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="57c7e-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="57c7e-108">Zwraca adres stosu wewnętrznego ramki.</span><span class="sxs-lookup"><span data-stu-id="57c7e-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="57c7e-109">IsCloserToLeaf, metoda</span><span class="sxs-lookup"><span data-stu-id="57c7e-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="57c7e-110">Sprawdza, czy `this` wewnętrzny ramki jest bliżej niż określony obiekt ICorDebugFrame liścia.</span><span class="sxs-lookup"><span data-stu-id="57c7e-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57c7e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57c7e-111">Remarks</span></span>  
 <span data-ttu-id="57c7e-112">Ten interfejs umożliwia rozbudowywanie interfejsu ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="57c7e-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57c7e-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="57c7e-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c7e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57c7e-114">Requirements</span></span>  
 <span data-ttu-id="57c7e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57c7e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c7e-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57c7e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57c7e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57c7e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57c7e-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c7e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57c7e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57c7e-119">See Also</span></span>  
 [<span data-ttu-id="57c7e-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="57c7e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="57c7e-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="57c7e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
