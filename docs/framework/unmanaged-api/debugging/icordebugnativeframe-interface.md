---
title: ICorDebugNativeFrame — Interfejs
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
ms.openlocfilehash: 04bdbc49217236bc6c05a718cb4d42067cafd8bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096671"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="e88ca-102">ICorDebugNativeFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e88ca-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="e88ca-103">Wyspecjalizowana implementacja ICorDebugFrame używana w przypadku ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="e88ca-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e88ca-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e88ca-104">Methods</span></span>  
  
|<span data-ttu-id="e88ca-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-105">Method</span></span>|<span data-ttu-id="e88ca-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e88ca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e88ca-107">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="e88ca-108">Pobiera wartość wskazującą, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="e88ca-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="e88ca-109">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="e88ca-110">Pobiera przesunięcie ramki stosu do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="e88ca-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="e88ca-111">GetLocalDoubleRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="e88ca-112">Pobiera wskaźnik do elementu ICorDebugValue, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch rejestrach pamięci ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="e88ca-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="e88ca-113">GetLocalMemoryRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="e88ca-114">Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość zmiennej lokalnej, w której niskie bity są przechowywane w określonym rejestrze, a duże bity są przechowywane przy określonym adresie pamięci.</span><span class="sxs-lookup"><span data-stu-id="e88ca-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="e88ca-115">GetLocalMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="e88ca-116">Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość zmiennej lokalnej przechowywanej w określonym adresie pamięci.</span><span class="sxs-lookup"><span data-stu-id="e88ca-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="e88ca-117">GetLocalRegisterMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="e88ca-118">Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość zmiennej lokalnej, w której duże bity są przechowywane w określonym rejestrze, a niskie bity są przechowywane w określonym adresie pamięci</span><span class="sxs-lookup"><span data-stu-id="e88ca-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="e88ca-119">GetLocalRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="e88ca-120">Pobiera wskaźnik do `ICorDebugValue`, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze macierzystym.</span><span class="sxs-lookup"><span data-stu-id="e88ca-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="e88ca-121">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="e88ca-122">Pobiera wskaźnik do elementu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla tego `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="e88ca-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="e88ca-123">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="e88ca-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="e88ca-124">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="e88ca-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e88ca-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e88ca-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e88ca-126">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e88ca-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e88ca-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e88ca-127">Requirements</span></span>  
 <span data-ttu-id="e88ca-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e88ca-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e88ca-129">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e88ca-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e88ca-130">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e88ca-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e88ca-131">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e88ca-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e88ca-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e88ca-132">See also</span></span>

- [<span data-ttu-id="e88ca-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e88ca-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
