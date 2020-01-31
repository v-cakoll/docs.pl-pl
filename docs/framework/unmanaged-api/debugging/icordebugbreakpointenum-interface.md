---
title: ICorDebugBreakpointEnum, interfejs
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
ms.openlocfilehash: 22ae1d24040a8ee5000e0ff2fbeb2b45e08050df
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784345"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="f0cf4-102">ICorDebugBreakpointEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0cf4-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="f0cf4-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0cf4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f0cf4-104">Methods</span></span>  
  
|<span data-ttu-id="f0cf4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0cf4-105">Method</span></span>|<span data-ttu-id="f0cf4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f0cf4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0cf4-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="f0cf4-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="f0cf4-108">Pobiera określoną liczbę wystąpień `ICorDebugBreakpoint` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0cf4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0cf4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0cf4-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f0cf4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0cf4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0cf4-111">Requirements</span></span>  
 <span data-ttu-id="f0cf4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0cf4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0cf4-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f0cf4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0cf4-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f0cf4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0cf4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0cf4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cf4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0cf4-116">See also</span></span>

- [<span data-ttu-id="f0cf4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0cf4-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
