---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1db53f50e942e70517fc06dfd90e75d04158ea9a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe-interface1"></a><span data-ttu-id="cb6d1-102">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="cb6d1-102">ICorDebugILFrame Interface1</span></span>
<span data-ttu-id="cb6d1-103">Reprezentuje ramka stosu kodu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="cb6d1-104">Ten interfejs jest podklasą klasy interfejsu ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cb6d1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cb6d1-105">Methods</span></span>  
  
|<span data-ttu-id="cb6d1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-106">Method</span></span>|<span data-ttu-id="cb6d1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cb6d1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cb6d1-108">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="cb6d1-109">Pobiera wartość wskazującą, czy jest to bezpieczne ustawienia wskaźnika instrukcji w określonej lokalizacji przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="cb6d1-110">EnumerateArguments, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="cb6d1-111">Pobiera moduł wyliczający dla argumentów do tej ramki.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="cb6d1-112">EnumerateLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="cb6d1-113">Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="cb6d1-114">GetArgument, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="cb6d1-115">Pobiera wartość określonego argumentu w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="cb6d1-116">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="cb6d1-117">Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, opisujące, jak uzyskano wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="cb6d1-118">GetLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="cb6d1-119">Pobiera wartość zmiennej lokalnej określony w tej ramki stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="cb6d1-120">GetStackDepth, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="cb6d1-121">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-121">Not implemented.</span></span>|  
|[<span data-ttu-id="cb6d1-122">GetStackValue, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="cb6d1-123">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-123">Not implemented.</span></span>|  
|[<span data-ttu-id="cb6d1-124">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="cb6d1-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="cb6d1-125">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb6d1-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb6d1-126">Remarks</span></span>  
 <span data-ttu-id="cb6d1-127">`ICorDebugILFrame` Interfejs jest interfejsem ICorDebugFrame specjalne.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="cb6d1-128">Jest ona używana zarówno dla ramki kod MSIL i just-in-time (JIT) skompilowany ramki.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="cb6d1-129">Ramki kompilacji JIT implementować jednocześnie `ICorDebugILFrame` i interfejsem ICorDebugNativeFrame.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb6d1-130">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="cb6d1-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb6d1-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb6d1-131">Requirements</span></span>  
 <span data-ttu-id="cb6d1-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb6d1-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb6d1-133">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb6d1-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb6d1-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb6d1-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb6d1-135">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb6d1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6d1-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb6d1-136">See Also</span></span>  
 [<span data-ttu-id="cb6d1-137">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cb6d1-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
