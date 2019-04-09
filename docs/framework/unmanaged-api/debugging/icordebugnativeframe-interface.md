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
ms.openlocfilehash: 2d59450540b680d6004c47fd646769e38c806024
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161268"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="9da56-102">ICorDebugNativeFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="9da56-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="9da56-103">Wyspecjalizowana implementacja ICorDebugFrame wykorzystywana do ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="9da56-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9da56-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9da56-104">Methods</span></span>  
  
|<span data-ttu-id="9da56-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-105">Method</span></span>|<span data-ttu-id="9da56-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9da56-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9da56-107">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="9da56-108">Pobiera wartość wskazującą, czy jest bezpiecznie Ustaw wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="9da56-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="9da56-109">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="9da56-110">Pobiera przesunięcie ramki stosu w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="9da56-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="9da56-111">GetLocalDoubleRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="9da56-112">Pobiera wskaźnik do ICorDebugValue, która reprezentuje wartość argumentu lub zmiennej lokalnej, przechowywane w dwóch rejestrów pamięci ramka natywna.</span><span class="sxs-lookup"><span data-stu-id="9da56-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="9da56-113">GetLocalMemoryRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="9da56-114">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość zmiennej lokalnej, z których niski bity są przechowywane w określonej rejestru i starsze bity są przechowywane na adres pamięci określonej.</span><span class="sxs-lookup"><span data-stu-id="9da56-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="9da56-115">GetLocalMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="9da56-116">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość przechowywaną w adres pamięci określonej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="9da56-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="9da56-117">GetLocalRegisterMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="9da56-118">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość zmiennej lokalnej, którego starsze bity są przechowywane w określonej rejestru i niski bity są przechowywane pod adresem określonym pamięci</span><span class="sxs-lookup"><span data-stu-id="9da56-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="9da56-119">GetLocalRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="9da56-120">Pobiera wskaźnik do `ICorDebugValue` reprezentująca wartość argumentu lub zmiennej lokalnej, przechowywane w określonej rejestru macierzystego.</span><span class="sxs-lookup"><span data-stu-id="9da56-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="9da56-121">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="9da56-122">Pobiera wskaźnik do [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) reprezentujący rejestru, określić dla niej `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="9da56-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="9da56-123">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="9da56-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="9da56-124">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="9da56-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9da56-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9da56-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9da56-126">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="9da56-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9da56-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9da56-127">Requirements</span></span>  
 <span data-ttu-id="9da56-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9da56-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9da56-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9da56-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9da56-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9da56-130">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9da56-131">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9da56-131">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9da56-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9da56-132">See also</span></span>

- [<span data-ttu-id="9da56-133">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9da56-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
