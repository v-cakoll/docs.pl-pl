---
title: ICorDebugStepperEnum — Interfejs
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
ms.openlocfilehash: feaf5bd25e276bb93c076f200912965c612af453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139002"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="610f0-102">ICorDebugStepperEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="610f0-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="610f0-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="610f0-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="610f0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="610f0-104">Methods</span></span>  
  
|<span data-ttu-id="610f0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="610f0-105">Method</span></span>|<span data-ttu-id="610f0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="610f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="610f0-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="610f0-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="610f0-108">Pobiera określoną liczbę wystąpień `ICorDebugStepper` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="610f0-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="610f0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="610f0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="610f0-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="610f0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="610f0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="610f0-111">Requirements</span></span>  
 <span data-ttu-id="610f0-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="610f0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="610f0-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="610f0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="610f0-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="610f0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="610f0-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="610f0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610f0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="610f0-116">See also</span></span>

- [<span data-ttu-id="610f0-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="610f0-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
