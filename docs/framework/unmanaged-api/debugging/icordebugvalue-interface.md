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
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966861"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="e3ec5-102">ICorDebugValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ec5-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="e3ec5-103">Reprezentuje wartość w debugowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="e3ec5-104">Wartość może być wartością odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3ec5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e3ec5-105">Methods</span></span>  
  
|<span data-ttu-id="e3ec5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e3ec5-106">Method</span></span>|<span data-ttu-id="e3ec5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3ec5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3ec5-108">CreateBreakpoint, metoda</span><span class="sxs-lookup"><span data-stu-id="e3ec5-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="e3ec5-109">Ta metoda nie jest obecnie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="e3ec5-110">GetAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="e3ec5-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="e3ec5-111">Pobiera adres tego `ICorDebugValue` obiektu, który jest w trakcie debugowania.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="e3ec5-112">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="e3ec5-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="e3ec5-113">Pobiera rozmiar tego `ICorDebugValue` obiektu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="e3ec5-114">GetType, metoda</span><span class="sxs-lookup"><span data-stu-id="e3ec5-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="e3ec5-115">Pobiera typ pierwotny tego `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3ec5-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3ec5-116">Remarks</span></span>  
 <span data-ttu-id="e3ec5-117">Ogólnie rzecz biorąc, własność obiektu wartości jest przenoszona, gdy jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="e3ec5-118">Odbiorca jest odpowiedzialny za usunięcie odwołania z obiektu po zakończeniu z obiektem.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="e3ec5-119">W zależności od tego, skąd została pobrana wartość, wartość może nie być ważna po wznowieniu procesu.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="e3ec5-120">Dlatego ogólnie rzecz biorąc wartość nie powinna być utrzymywana przez wywołanie metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e3ec5-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3ec5-121">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e3ec5-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3ec5-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3ec5-122">Requirements</span></span>  
 <span data-ttu-id="e3ec5-123">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3ec5-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3ec5-124">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3ec5-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3ec5-125">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3ec5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3ec5-126">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3ec5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3ec5-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3ec5-127">See also</span></span>

- [<span data-ttu-id="e3ec5-128">ICorDebugValue3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3ec5-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="e3ec5-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e3ec5-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
