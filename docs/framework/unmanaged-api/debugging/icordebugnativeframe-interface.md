---
title: ICorDebugNativeFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame
helpviewer_keywords: ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 63d631dec00e63d6ee383cd36d79382a529d9ddb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframe-interface1"></a><span data-ttu-id="5b48b-102">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="5b48b-102">ICorDebugNativeFrame Interface1</span></span>
<span data-ttu-id="5b48b-103">Specjalne implementacja ICorDebugFrame używany dla ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="5b48b-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b48b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5b48b-104">Methods</span></span>  
  
|<span data-ttu-id="5b48b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-105">Method</span></span>|<span data-ttu-id="5b48b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5b48b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b48b-107">CanSetIP — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="5b48b-108">Pobiera wartość wskazującą, czy jest to bezpieczne ustawienia wskaźnika instrukcji w określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="5b48b-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="5b48b-109">GetIP — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="5b48b-110">Pobiera przesunięcie ramki stosu w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="5b48b-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="5b48b-111">GetLocalDoubleRegisterValue — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="5b48b-112">Pobiera wskaźnik do ICorDebugValue reprezentujący wartość argumentu lub zmienna lokalna przechowywane w dwóch rejestrów pamięci ramka natywna.</span><span class="sxs-lookup"><span data-stu-id="5b48b-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="5b48b-113">GetLocalMemoryRegisterValue — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="5b48b-114">Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość zmiennej lokalnej, którego niski bity są przechowywane w rejestrze określonego i bitów znajdują się pod adresem określonym pamięci.</span><span class="sxs-lookup"><span data-stu-id="5b48b-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="5b48b-115">GetLocalMemoryValue — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="5b48b-116">Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość zmiennej lokalnej przechowywane pod adresem określonym pamięci.</span><span class="sxs-lookup"><span data-stu-id="5b48b-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="5b48b-117">GetLocalRegisterMemoryValue — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="5b48b-118">Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość zmiennej lokalnej, którego bitów są przechowywane w rejestrze określonego i niski bity są przechowywane pod adresem określonym pamięci</span><span class="sxs-lookup"><span data-stu-id="5b48b-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="5b48b-119">GetLocalRegisterValue — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="5b48b-120">Pobiera wskaźnik do `ICorDebugValue` reprezentujący wartość argumentu lub przechowywane w rejestrze natywnego określonej zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="5b48b-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="5b48b-121">GetRegisterSet — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="5b48b-122">Pobiera wskaźnik do [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) reprezentujący rejestru ustawić dla tego `ICorDebugNativeFrame`.</span><span class="sxs-lookup"><span data-stu-id="5b48b-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="5b48b-123">SetIP — metoda</span><span class="sxs-lookup"><span data-stu-id="5b48b-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="5b48b-124">Ustawia wskaźnik instrukcji w określonej lokalizacji przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="5b48b-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b48b-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b48b-125">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b48b-126">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="5b48b-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b48b-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b48b-127">Requirements</span></span>  
 <span data-ttu-id="5b48b-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b48b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b48b-129">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b48b-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b48b-130">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b48b-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b48b-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b48b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b48b-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b48b-132">See Also</span></span>  
 [<span data-ttu-id="5b48b-133">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="5b48b-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
