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
ms.openlocfilehash: b8d2e49031e59db0527de3c848d7d390095797bf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396793"
---
# <a name="icordebugvalue-interface"></a><span data-ttu-id="10e29-102">ICorDebugValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="10e29-102">ICorDebugValue Interface</span></span>
<span data-ttu-id="10e29-103">Reprezentuje wartość w debugowanym procesie.</span><span class="sxs-lookup"><span data-stu-id="10e29-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="10e29-104">Wartość może być wartością odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="10e29-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10e29-105">Metody</span><span class="sxs-lookup"><span data-stu-id="10e29-105">Methods</span></span>  
  
|<span data-ttu-id="10e29-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="10e29-106">Method</span></span>|<span data-ttu-id="10e29-107">Opis</span><span class="sxs-lookup"><span data-stu-id="10e29-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10e29-108">CreateBreakpoint — Metoda</span><span class="sxs-lookup"><span data-stu-id="10e29-108">CreateBreakpoint Method</span></span>](icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="10e29-109">Ta metoda nie jest obecnie zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="10e29-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="10e29-110">GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="10e29-110">GetAddress Method</span></span>](icordebugvalue-getaddress-method.md)|<span data-ttu-id="10e29-111">Pobiera adres tego `ICorDebugValue` obiektu, który jest w trakcie debugowania.</span><span class="sxs-lookup"><span data-stu-id="10e29-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="10e29-112">GetSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="10e29-112">GetSize Method</span></span>](icordebugvalue-getsize-method.md)|<span data-ttu-id="10e29-113">Pobiera rozmiar tego obiektu w bajtach `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="10e29-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="10e29-114">GetType, metoda</span><span class="sxs-lookup"><span data-stu-id="10e29-114">GetType Method</span></span>](icordebugvalue-gettype-method.md)|<span data-ttu-id="10e29-115">Pobiera typ pierwotny tego `ICorDebugValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="10e29-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10e29-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10e29-116">Remarks</span></span>  
 <span data-ttu-id="10e29-117">Ogólnie rzecz biorąc, własność obiektu wartości jest przenoszona, gdy jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="10e29-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="10e29-118">Odbiorca jest odpowiedzialny za usunięcie odwołania z obiektu po zakończeniu z obiektem.</span><span class="sxs-lookup"><span data-stu-id="10e29-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="10e29-119">W zależności od tego, skąd została pobrana wartość, wartość może nie być ważna po wznowieniu procesu.</span><span class="sxs-lookup"><span data-stu-id="10e29-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="10e29-120">Dlatego ogólnie rzecz biorąc wartość nie powinna być utrzymywana przez wywołanie metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .</span><span class="sxs-lookup"><span data-stu-id="10e29-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10e29-121">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="10e29-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10e29-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="10e29-122">Requirements</span></span>  
 <span data-ttu-id="10e29-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10e29-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10e29-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="10e29-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10e29-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="10e29-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10e29-126">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10e29-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10e29-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="10e29-127">See also</span></span>

- [<span data-ttu-id="10e29-128">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="10e29-128">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
- [<span data-ttu-id="10e29-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="10e29-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
