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
ms.openlocfilehash: 256f67d21a22ee4692d88311cc150736e61563a0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073070"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="cb2cb-102">ICorDebugStepper2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb2cb-102">ICorDebugStepper2 Interface</span></span>
<span data-ttu-id="cb2cb-103">Zapewnia obsługę tylko mój kod (JMC) debugowania.</span><span class="sxs-lookup"><span data-stu-id="cb2cb-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb2cb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cb2cb-104">Methods</span></span>  
  
|<span data-ttu-id="cb2cb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb2cb-105">Method</span></span>|<span data-ttu-id="cb2cb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cb2cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb2cb-107">SetJMC, metoda</span><span class="sxs-lookup"><span data-stu-id="cb2cb-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="cb2cb-108">Ustawia wartość określającą, czy ten ICorDebugStepper — przeprowadzi tylko kod, który został utworzony przez dewelopera aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb2cb-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb2cb-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb2cb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb2cb-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="cb2cb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb2cb-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb2cb-111">Requirements</span></span>  
 <span data-ttu-id="cb2cb-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb2cb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb2cb-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb2cb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb2cb-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb2cb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb2cb-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb2cb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb2cb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb2cb-116">See also</span></span>

- [<span data-ttu-id="cb2cb-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cb2cb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
