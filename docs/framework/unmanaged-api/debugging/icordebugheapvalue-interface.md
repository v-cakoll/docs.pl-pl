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
ms.openlocfilehash: 4f87065fc4a3d80a8363f3ae2fbb76c29f3d9b96
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138419"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="8ada2-102">ICorDebugHeapValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8ada2-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="8ada2-103">Podklasa elementu "ICorDebugValue" reprezentująca obiekt, który został zebrany przez moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="8ada2-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ada2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8ada2-104">Methods</span></span>  
  
|<span data-ttu-id="8ada2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ada2-105">Method</span></span>|<span data-ttu-id="8ada2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8ada2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ada2-107">CreateRelocBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="8ada2-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="8ada2-108">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="8ada2-108">Not implemented.</span></span>|  
|[<span data-ttu-id="8ada2-109">IsValid, metoda</span><span class="sxs-lookup"><span data-stu-id="8ada2-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="8ada2-110">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` jest prawidłowy, czy został odrzucony przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="8ada2-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="8ada2-111">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="8ada2-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ada2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ada2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ada2-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="8ada2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ada2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ada2-114">Requirements</span></span>  
 <span data-ttu-id="8ada2-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ada2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ada2-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ada2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ada2-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8ada2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ada2-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ada2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ada2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ada2-119">See also</span></span>

- [<span data-ttu-id="8ada2-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8ada2-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
