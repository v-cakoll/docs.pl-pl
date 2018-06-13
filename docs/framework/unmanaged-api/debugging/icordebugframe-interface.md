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
ms.openlocfilehash: f3d6c1a2bfd66e275b506d4465731c48cd7c6515
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416634"
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="6006c-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="6006c-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="6006c-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="6006c-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6006c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6006c-104">Methods</span></span>  
  
|<span data-ttu-id="6006c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-105">Method</span></span>|<span data-ttu-id="6006c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6006c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6006c-107">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="6006c-108">Pobiera ICorDebugStepper — w celu wykonania operacji wykonywania krokowego względem to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="6006c-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="6006c-109">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="6006c-110">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego czy wywołać tej ramki, lub zwraca wartość null, jeśli to jest najbardziej ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="6006c-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="6006c-111">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="6006c-112">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego, która o nazwie tej ramki lub zwraca wartość null, jeśli to jest najbardziej zewnętrznego ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="6006c-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="6006c-113">GetChain, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="6006c-114">Pobiera wskaźnik do ICorDebugChain to `ICorDebugFrame` jest częścią.</span><span class="sxs-lookup"><span data-stu-id="6006c-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="6006c-115">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="6006c-116">Pobiera wskaźnik do ICorDebugCode skojarzone z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="6006c-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="6006c-117">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="6006c-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="6006c-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="6006c-119">GetFunctionToken, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="6006c-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="6006c-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="6006c-121">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="6006c-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="6006c-122">Pobiera adres bezwzględny zakres ramki stosu reprezentowany przez ten `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="6006c-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6006c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6006c-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6006c-124">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="6006c-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6006c-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6006c-125">Requirements</span></span>  
 <span data-ttu-id="6006c-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6006c-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6006c-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6006c-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6006c-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6006c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6006c-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6006c-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6006c-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6006c-130">See Also</span></span>  
 [<span data-ttu-id="6006c-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6006c-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
