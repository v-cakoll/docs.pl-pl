---
title: ICorDebugNativeFrame, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c01346b42fff812f8358482ae0e8570c03ee9231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912802"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="c99cc-102">ICorDebugNativeFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="c99cc-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="c99cc-103">Wyspecjalizowana implementacja ICorDebugFrame używana w przypadku ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="c99cc-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c99cc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c99cc-104">Methods</span></span>  
  
|<span data-ttu-id="c99cc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-105">Method</span></span>|<span data-ttu-id="c99cc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c99cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c99cc-107">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="c99cc-108">Pobiera wartość wskazującą, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c99cc-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="c99cc-109">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="c99cc-110">Pobiera przesunięcie ramki stosu do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="c99cc-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="c99cc-111">GetLocalDoubleRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="c99cc-112">Pobiera wskaźnik do elementu ICorDebugValue, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch rejestrach pamięci ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="c99cc-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="c99cc-113">GetLocalMemoryRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="c99cc-114">Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której niskie bity są przechowywane w określonym rejestrze, a duże bity są przechowywane w określonym adresie pamięci.</span><span class="sxs-lookup"><span data-stu-id="c99cc-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="c99cc-115">GetLocalMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="c99cc-116">Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej przechowywanej w określonym adresie pamięci.</span><span class="sxs-lookup"><span data-stu-id="c99cc-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="c99cc-117">GetLocalRegisterMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="c99cc-118">Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której duże bity są przechowywane w określonym rejestrze, a niskie bity są przechowywane w określonym adresie pamięci</span><span class="sxs-lookup"><span data-stu-id="c99cc-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="c99cc-119">GetLocalRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="c99cc-120">Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze macierzystym.</span><span class="sxs-lookup"><span data-stu-id="c99cc-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="c99cc-121">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="c99cc-122">Pobiera wskaźnik do elementu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla tego `ICorDebugNativeFrame`elementu.</span><span class="sxs-lookup"><span data-stu-id="c99cc-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="c99cc-123">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="c99cc-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="c99cc-124">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="c99cc-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c99cc-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c99cc-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c99cc-126">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="c99cc-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c99cc-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c99cc-127">Requirements</span></span>  
 <span data-ttu-id="c99cc-128">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c99cc-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c99cc-129">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c99cc-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c99cc-130">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c99cc-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c99cc-131">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c99cc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99cc-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c99cc-132">See also</span></span>

- [<span data-ttu-id="c99cc-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c99cc-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
