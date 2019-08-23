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
ms.openlocfilehash: eb130f11975eb95db7807126d6f163425439b0c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914898"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="8c57b-102">ICorDebugHeapValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="8c57b-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="8c57b-103">Podklasa elementu "ICorDebugValue" reprezentująca obiekt, który został zebrany przez moduł zbierający elementy bezużyteczne środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="8c57b-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c57b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8c57b-104">Methods</span></span>  
  
|<span data-ttu-id="8c57b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8c57b-105">Method</span></span>|<span data-ttu-id="8c57b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8c57b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c57b-107">CreateRelocBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="8c57b-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="8c57b-108">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="8c57b-108">Not implemented.</span></span>|  
|[<span data-ttu-id="8c57b-109">IsValid, metoda</span><span class="sxs-lookup"><span data-stu-id="8c57b-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="8c57b-110">Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` element jest prawidłowy lub został odrzucony przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="8c57b-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="8c57b-111">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c57b-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c57b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c57b-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c57b-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="8c57b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c57b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c57b-114">Requirements</span></span>  
 <span data-ttu-id="8c57b-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c57b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c57b-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c57b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c57b-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c57b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c57b-118">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c57b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c57b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c57b-119">See also</span></span>

- [<span data-ttu-id="8c57b-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8c57b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
