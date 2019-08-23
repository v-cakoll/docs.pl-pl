---
title: ICorDebugStepperEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum
helpviewer_keywords:
- ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7336f958019c2f696a9b1a26b075c076cfc84f5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953020"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="c755e-102">ICorDebugStepperEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="c755e-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="c755e-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="c755e-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c755e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c755e-104">Methods</span></span>  
  
|<span data-ttu-id="c755e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c755e-105">Method</span></span>|<span data-ttu-id="c755e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c755e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c755e-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="c755e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="c755e-108">Pobiera określoną liczbę `ICorDebugStepper` wystąpień z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="c755e-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c755e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c755e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c755e-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="c755e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c755e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c755e-111">Requirements</span></span>  
 <span data-ttu-id="c755e-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c755e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c755e-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c755e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c755e-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c755e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c755e-115">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c755e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c755e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c755e-116">See also</span></span>

- [<span data-ttu-id="c755e-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c755e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
