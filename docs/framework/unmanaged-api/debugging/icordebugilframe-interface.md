---
title: ICorDebugILFrame, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c60d7685de1e9a1d4f631ad1fba53b981829f58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159805"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="c305c-102">ICorDebugILFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="c305c-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="c305c-103">Reprezentuje ramkę stosu kodu języka intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c305c-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="c305c-104">Ten interfejs jest podklasą icordebugframe — interfejs.</span><span class="sxs-lookup"><span data-stu-id="c305c-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c305c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c305c-105">Methods</span></span>  
  
|<span data-ttu-id="c305c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-106">Method</span></span>|<span data-ttu-id="c305c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c305c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c305c-108">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-108">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|<span data-ttu-id="c305c-109">Pobiera wartość wskazującą, czy jest bezpiecznie Ustaw wskaźnik instrukcji do określonej lokalizacji przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="c305c-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="c305c-110">EnumerateArguments, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-110">EnumerateArguments Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="c305c-111">Pobiera moduł wyliczający dla argumentów w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="c305c-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="c305c-112">EnumerateLocalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-112">EnumerateLocalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="c305c-113">Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="c305c-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="c305c-114">GetArgument, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-114">GetArgument Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|<span data-ttu-id="c305c-115">Pobiera wartość określonego argumentu w tej ramce stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="c305c-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="c305c-116">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-116">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|<span data-ttu-id="c305c-117">Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, w tym artykule opisano, jak wartość wskaźnika instrukcji zostały pobrane.</span><span class="sxs-lookup"><span data-stu-id="c305c-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="c305c-118">GetLocalVariable, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-118">GetLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="c305c-119">Pobiera wartość określonej zmiennej lokalnej w tej ramki stosu MSIL.</span><span class="sxs-lookup"><span data-stu-id="c305c-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="c305c-120">GetStackDepth, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-120">GetStackDepth Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="c305c-121">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="c305c-121">Not implemented.</span></span>|  
|[<span data-ttu-id="c305c-122">GetStackValue, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-122">GetStackValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="c305c-123">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="c305c-123">Not implemented.</span></span>|  
|[<span data-ttu-id="c305c-124">SetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="c305c-124">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|<span data-ttu-id="c305c-125">Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="c305c-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c305c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c305c-126">Remarks</span></span>  
 <span data-ttu-id="c305c-127">`ICorDebugILFrame` Interfejs jest wyspecjalizowane icordebugframe — interfejs.</span><span class="sxs-lookup"><span data-stu-id="c305c-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="c305c-128">Jest używany zarówno dla ramki kodu MSIL i just-in-time (JIT) skompilowany ramek.</span><span class="sxs-lookup"><span data-stu-id="c305c-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="c305c-129">Kompilowanego dokładnie na czas ramki zaimplementować obu `ICorDebugILFrame` interfejsu i icordebugnativeframe — interfejs.</span><span class="sxs-lookup"><span data-stu-id="c305c-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c305c-130">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="c305c-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c305c-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c305c-131">Requirements</span></span>  
 <span data-ttu-id="c305c-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c305c-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c305c-133">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c305c-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c305c-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c305c-134">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c305c-135">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c305c-135">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c305c-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c305c-136">See also</span></span>

- [<span data-ttu-id="c305c-137">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c305c-137">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
