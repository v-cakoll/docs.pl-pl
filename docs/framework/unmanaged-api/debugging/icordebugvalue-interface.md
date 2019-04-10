---
title: ICorDebugValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc889dd6b2854654bfe43b24afbe4cc19863c80
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227824"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="69bad-102">ICorDebugValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="69bad-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="69bad-103">Reprezentuje wartość w debugowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="69bad-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="69bad-104">Wartość może być wartością zapisu lub odczytu.</span><span class="sxs-lookup"><span data-stu-id="69bad-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69bad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="69bad-105">Methods</span></span>  
  
|<span data-ttu-id="69bad-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="69bad-106">Method</span></span>|<span data-ttu-id="69bad-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69bad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69bad-108">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="69bad-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="69bad-109">Ta metoda nie jest obecnie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="69bad-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="69bad-110">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="69bad-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="69bad-111">Pobiera adres to `ICorDebugValue` obiektu, który jest w trakcie debugowania.</span><span class="sxs-lookup"><span data-stu-id="69bad-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="69bad-112">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="69bad-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="69bad-113">Pobiera rozmiar w bajtach to `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="69bad-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="69bad-114">GetType, metoda</span><span class="sxs-lookup"><span data-stu-id="69bad-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="69bad-115">Pobiera pierwotny typ `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="69bad-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69bad-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69bad-116">Remarks</span></span>  
 <span data-ttu-id="69bad-117">Ogólnie rzecz biorąc własność obiektu wartość jest przekazywana, gdy jest on zwracany.</span><span class="sxs-lookup"><span data-stu-id="69bad-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="69bad-118">Adresat jest odpowiedzialny za usunięcie odwołanie z obiektu po jego zakończeniu za pomocą obiektu.</span><span class="sxs-lookup"><span data-stu-id="69bad-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="69bad-119">W zależności od tego, gdzie wartość została pobrana z wartość może być pozostają w mocy po wznowieniu procesu.</span><span class="sxs-lookup"><span data-stu-id="69bad-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="69bad-120">Tak, ogólnie rzecz biorąc, wartość nie powinny być przechowywane przez wywołanie [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="69bad-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69bad-121">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="69bad-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69bad-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69bad-122">Requirements</span></span>  
 <span data-ttu-id="69bad-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69bad-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69bad-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="69bad-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69bad-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69bad-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="69bad-126">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="69bad-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="69bad-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69bad-127">See also</span></span>

- [<span data-ttu-id="69bad-128">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="69bad-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="69bad-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="69bad-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
