---
title: ICorDebugBreakpointEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 5fb4a8a508cde4455bbee8c08432d3549e3fac43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122757"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="ec748-102">ICorDebugBreakpointEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ec748-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="ec748-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="ec748-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ec748-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ec748-104">Methods</span></span>  
  
|<span data-ttu-id="ec748-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ec748-105">Method</span></span>|<span data-ttu-id="ec748-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ec748-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ec748-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="ec748-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="ec748-108">Pobiera określoną liczbę wystąpień `ICorDebugBreakpoint` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="ec748-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec748-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec748-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec748-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="ec748-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec748-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec748-111">Requirements</span></span>  
 <span data-ttu-id="ec748-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec748-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec748-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec748-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec748-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec748-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec748-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec748-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec748-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec748-116">See also</span></span>

- [<span data-ttu-id="ec748-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ec748-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
