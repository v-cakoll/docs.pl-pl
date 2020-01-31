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
ms.openlocfilehash: aa0ff0ff7c8fe32f181fb86ee5b778ea618df3b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791703"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="3180c-102">ICorDebugStepperEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="3180c-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="3180c-103">Implementuje metody ICorDebugEnum i wylicza tablice ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="3180c-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3180c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3180c-104">Methods</span></span>  
  
|<span data-ttu-id="3180c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3180c-105">Method</span></span>|<span data-ttu-id="3180c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3180c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3180c-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="3180c-107">Next Method</span></span>](icordebugstepperenum-next-method.md)|<span data-ttu-id="3180c-108">Pobiera określoną liczbę wystąpień `ICorDebugStepper` z wyliczenia, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="3180c-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3180c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3180c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3180c-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="3180c-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3180c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3180c-111">Requirements</span></span>  
 <span data-ttu-id="3180c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3180c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3180c-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3180c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3180c-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3180c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3180c-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3180c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3180c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3180c-116">See also</span></span>

- [<span data-ttu-id="3180c-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3180c-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
