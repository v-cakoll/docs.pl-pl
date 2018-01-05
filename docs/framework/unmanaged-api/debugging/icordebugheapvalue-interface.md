---
title: ICorDebugHeapValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue
helpviewer_keywords: ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2ab132b73369526204f8fd811e1567b07b4a9b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="6d995-102">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="6d995-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="6d995-103">Podklasa "ICorDebugValue", który reprezentuje obiekt, które zostały zebrane przez wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6d995-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d995-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6d995-104">Methods</span></span>  
  
|<span data-ttu-id="6d995-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d995-105">Method</span></span>|<span data-ttu-id="6d995-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6d995-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d995-107">CreateRelocBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="6d995-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="6d995-108">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="6d995-108">Not implemented.</span></span>|  
|[<span data-ttu-id="6d995-109">IsValid, metoda</span><span class="sxs-lookup"><span data-stu-id="6d995-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="6d995-110">Pobiera wartość wskazującą, czy obiekt reprezentowany przez to `ICorDebugHeapValue` jest nieprawidłowy lub ma zostać odzyskana przez moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6d995-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="6d995-111">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="6d995-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d995-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d995-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d995-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="6d995-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d995-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d995-114">Requirements</span></span>  
 <span data-ttu-id="6d995-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d995-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d995-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d995-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d995-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d995-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d995-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d995-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d995-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d995-119">See Also</span></span>  
    
    
    
 [<span data-ttu-id="6d995-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d995-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
