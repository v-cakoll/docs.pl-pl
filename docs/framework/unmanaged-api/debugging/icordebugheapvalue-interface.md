---
title: ICorDebugHeapValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5263474b7b5001d561652291c23220da0a942bd1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980571"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="e9b42-102">ICorDebugHeapValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e9b42-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="e9b42-103">Podklasa klasy "ICorDebugValue", który reprezentuje obiekt, który został zebrany przez moduł odśmiecania pamięci środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e9b42-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9b42-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e9b42-104">Methods</span></span>  
  
|<span data-ttu-id="e9b42-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e9b42-105">Method</span></span>|<span data-ttu-id="e9b42-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e9b42-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9b42-107">CreateRelocBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="e9b42-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="e9b42-108">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="e9b42-108">Not implemented.</span></span>|  
|[<span data-ttu-id="e9b42-109">IsValid, metoda</span><span class="sxs-lookup"><span data-stu-id="e9b42-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="e9b42-110">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` jest prawidłowy lub został odzyskany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="e9b42-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="e9b42-111">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="e9b42-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9b42-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9b42-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9b42-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="e9b42-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9b42-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9b42-114">Requirements</span></span>  
 <span data-ttu-id="e9b42-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9b42-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9b42-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9b42-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9b42-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9b42-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9b42-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9b42-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b42-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9b42-119">See also</span></span>



- [<span data-ttu-id="e9b42-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e9b42-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
