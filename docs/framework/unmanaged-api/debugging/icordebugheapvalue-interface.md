---
title: ICorDebugHeapValue, interfejs
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
ms.openlocfilehash: d5fcd8c17c4006714fa9d11aece5cccc57c97087
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075499"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="b8cf7-102">ICorDebugHeapValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8cf7-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="b8cf7-103">Podklasa klasy "ICorDebugValue", który reprezentuje obiekt, który został zebrany przez moduł odśmiecania pamięci środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b8cf7-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8cf7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b8cf7-104">Methods</span></span>  
  
|<span data-ttu-id="b8cf7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b8cf7-105">Method</span></span>|<span data-ttu-id="b8cf7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b8cf7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8cf7-107">CreateRelocBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="b8cf7-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="b8cf7-108">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="b8cf7-108">Not implemented.</span></span>|  
|[<span data-ttu-id="b8cf7-109">IsValid, metoda</span><span class="sxs-lookup"><span data-stu-id="b8cf7-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="b8cf7-110">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` jest prawidłowy lub został odzyskany przez moduł odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8cf7-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="b8cf7-111">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b8cf7-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8cf7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8cf7-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8cf7-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="b8cf7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8cf7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8cf7-114">Requirements</span></span>  
 <span data-ttu-id="b8cf7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8cf7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8cf7-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8cf7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8cf7-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8cf7-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b8cf7-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b8cf7-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b8cf7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8cf7-119">See also</span></span>

- [<span data-ttu-id="b8cf7-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b8cf7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
