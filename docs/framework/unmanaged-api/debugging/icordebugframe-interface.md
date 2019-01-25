---
title: ICorDebugFrame Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f160612e499ca7bd2185c95aa07a3784c5a4a19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635757"
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="66c83-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="66c83-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="66c83-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="66c83-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66c83-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66c83-104">Methods</span></span>  
  
|<span data-ttu-id="66c83-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-105">Method</span></span>|<span data-ttu-id="66c83-106">Opis</span><span class="sxs-lookup"><span data-stu-id="66c83-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66c83-107">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="66c83-108">Pobiera ICorDebugStepper — do wykonywania operacji przechodzenia krok po kroku względem to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="66c83-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="66c83-109">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="66c83-110">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącej, że tej ramki o nazwie lub zwraca wartość null, jeśli to jest najbardziej ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="66c83-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="66c83-111">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="66c83-112">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącej, o nazwie tej ramki lub zwraca wartość null, jeśli to jest najbardziej zewnętrznej ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="66c83-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="66c83-113">GetChain, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="66c83-114">Pobiera wskaźnik do icordebugchain — `ICorDebugFrame` jest częścią.</span><span class="sxs-lookup"><span data-stu-id="66c83-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="66c83-115">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="66c83-116">Pobiera wskaźnik do ICorDebugCode skojarzone z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="66c83-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="66c83-117">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="66c83-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="66c83-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="66c83-119">GetFunctionToken, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="66c83-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="66c83-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="66c83-121">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="66c83-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="66c83-122">Pobiera bezwzględny zakres adresów ramki stosu, reprezentowane przez to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="66c83-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66c83-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66c83-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="66c83-124">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="66c83-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c83-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66c83-125">Requirements</span></span>  
 <span data-ttu-id="66c83-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c83-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c83-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66c83-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66c83-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66c83-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66c83-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c83-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c83-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66c83-130">See also</span></span>
- [<span data-ttu-id="66c83-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="66c83-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
