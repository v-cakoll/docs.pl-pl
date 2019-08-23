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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8192bd7ccaebab78158f11adb79509031132ecd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937019"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="f71e0-102">ICorDebugBreakpointEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="f71e0-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="f71e0-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="f71e0-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f71e0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f71e0-104">Methods</span></span>  
  
|<span data-ttu-id="f71e0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f71e0-105">Method</span></span>|<span data-ttu-id="f71e0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f71e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f71e0-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="f71e0-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="f71e0-108">Pobiera określoną liczbę `ICorDebugBreakpoint` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="f71e0-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f71e0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f71e0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f71e0-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="f71e0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f71e0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f71e0-111">Requirements</span></span>  
 <span data-ttu-id="f71e0-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f71e0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f71e0-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f71e0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f71e0-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f71e0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f71e0-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f71e0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71e0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f71e0-116">See also</span></span>

- [<span data-ttu-id="f71e0-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f71e0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
