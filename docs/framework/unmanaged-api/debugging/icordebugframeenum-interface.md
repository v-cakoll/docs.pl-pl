---
title: ICorDebugFrameEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
ms.openlocfilehash: 3a33d25ee13e12a2612d0132da1dc84c24f2f95b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090540"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="a26a2-102">ICorDebugFrameEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a26a2-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="a26a2-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="a26a2-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a26a2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a26a2-104">Methods</span></span>  
  
|<span data-ttu-id="a26a2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a26a2-105">Method</span></span>|<span data-ttu-id="a26a2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a26a2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a26a2-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="a26a2-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="a26a2-108">Pobiera określoną liczbę wystąpień `ICorDebugFrame` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="a26a2-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a26a2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a26a2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a26a2-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a26a2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a26a2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a26a2-111">Requirements</span></span>  
 <span data-ttu-id="a26a2-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a26a2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26a2-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a26a2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a26a2-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a26a2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a26a2-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26a2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26a2-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a26a2-116">See also</span></span>

- [<span data-ttu-id="a26a2-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a26a2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
