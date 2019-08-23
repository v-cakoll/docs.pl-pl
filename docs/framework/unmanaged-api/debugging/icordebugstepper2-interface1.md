---
title: ICorDebugStepper2, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d86f4bbec8971d164966298734388f0744a2d41c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953035"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="11b28-102">ICorDebugStepper2, interfejs</span><span class="sxs-lookup"><span data-stu-id="11b28-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="11b28-103">Zapewnia obsługę debugowania tylko mój kod (JMC).</span><span class="sxs-lookup"><span data-stu-id="11b28-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11b28-104">Metody</span><span class="sxs-lookup"><span data-stu-id="11b28-104">Methods</span></span>  
  
|<span data-ttu-id="11b28-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="11b28-105">Method</span></span>|<span data-ttu-id="11b28-106">Opis</span><span class="sxs-lookup"><span data-stu-id="11b28-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11b28-107">SetJMC, metoda</span><span class="sxs-lookup"><span data-stu-id="11b28-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="11b28-108">Ustawia wartość określającą, czy ten ICorDebugStepper czynności tylko za pomocą kodu, który jest tworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11b28-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11b28-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11b28-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11b28-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="11b28-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11b28-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11b28-111">Requirements</span></span>  
 <span data-ttu-id="11b28-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11b28-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11b28-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11b28-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11b28-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11b28-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11b28-115">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11b28-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11b28-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11b28-116">See also</span></span>

- [<span data-ttu-id="11b28-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="11b28-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
