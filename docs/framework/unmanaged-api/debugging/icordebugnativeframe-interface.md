---
title: ICorDebugNativeFrame Interface1
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
ms.openlocfilehash: c923b54f791cd8ff794538d4687ca0329e62c87e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547030"
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="f01c6-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="f01c6-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="f01c6-103">Wyspecjalizowana implementacja ICorDebugFrame wykorzystywana do ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="f01c6-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f01c6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f01c6-104">Methods</span></span>  
  
|<span data-ttu-id="f01c6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-105">Method</span></span>|<span data-ttu-id="f01c6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f01c6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f01c6-107">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="f01c6-108">Pobiera wartość wskazującą, czy jest bezpiecznie Ustaw wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="f01c6-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="f01c6-109">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="f01c6-110">Pobiera przesunięcie ramki stosu w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="f01c6-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="f01c6-111">GetLocalDoubleRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="f01c6-112">Pobiera wskaźnik do ICorDebugValue, która reprezentuje wartość argumentu lub zmiennej lokalnej, przechowywane w dwóch rejestrów pamięci ramka natywna.</span><span class="sxs-lookup"><span data-stu-id="f01c6-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="f01c6-113">GetLocalMemoryRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="f01c6-114">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość zmiennej lokalnej, z których niski bity są przechowywane w określonej rejestru i starsze bity są przechowywane na adres pamięci określonej.</span><span class="sxs-lookup"><span data-stu-id="f01c6-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="f01c6-115">GetLocalMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="f01c6-116">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość przechowywaną w adres pamięci określonej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="f01c6-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="f01c6-117">GetLocalRegisterMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="f01c6-118">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość zmiennej lokalnej, którego starsze bity są przechowywane w określonej rejestru i niski bity są przechowywane pod adresem określonym pamięci</span><span class="sxs-lookup"><span data-stu-id="f01c6-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="f01c6-119">GetLocalRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="f01c6-120">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość argumentu lub zmiennej lokalnej, przechowywane w określonej rejestru macierzystego.</span><span class="sxs-lookup"><span data-stu-id="f01c6-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="f01c6-121">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="f01c6-122">Pobiera wskaźnik do [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) reprezentujący rejestru, określić dla niej `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="f01c6-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="f01c6-123">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="f01c6-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="f01c6-124">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="f01c6-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f01c6-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f01c6-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f01c6-126">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f01c6-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f01c6-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f01c6-127">Requirements</span></span>  
 <span data-ttu-id="f01c6-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f01c6-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f01c6-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f01c6-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f01c6-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f01c6-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f01c6-131">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f01c6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f01c6-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f01c6-132">See also</span></span>
- [<span data-ttu-id="f01c6-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f01c6-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
