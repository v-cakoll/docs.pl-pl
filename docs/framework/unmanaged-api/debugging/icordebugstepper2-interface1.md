---
title: ICorDebugStepper2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: 28ec18864158641a337ebdea189080ba4247a7c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120523"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="70eb5-102">ICorDebugStepper2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="70eb5-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="70eb5-103">Zapewnia obsługę debugowania tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="70eb5-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70eb5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="70eb5-104">Methods</span></span>  
  
|<span data-ttu-id="70eb5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="70eb5-105">Method</span></span>|<span data-ttu-id="70eb5-106">Opis</span><span class="sxs-lookup"><span data-stu-id="70eb5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70eb5-107">SetJMC, metoda</span><span class="sxs-lookup"><span data-stu-id="70eb5-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="70eb5-108">Ustawia wartość określającą, czy ten ICorDebugStepper czynności tylko za pomocą kodu, który jest tworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="70eb5-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70eb5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70eb5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70eb5-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="70eb5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70eb5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70eb5-111">Requirements</span></span>  
 <span data-ttu-id="70eb5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70eb5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70eb5-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70eb5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70eb5-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="70eb5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70eb5-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70eb5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70eb5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70eb5-116">See also</span></span>

- [<span data-ttu-id="70eb5-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="70eb5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
