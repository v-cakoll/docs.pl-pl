---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: caa3ef9cd52cc872d4ebc96376c104a7b90fb4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="2680f-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="2680f-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="2680f-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="2680f-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2680f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2680f-104">Methods</span></span>  
  
|<span data-ttu-id="2680f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-105">Method</span></span>|<span data-ttu-id="2680f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2680f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2680f-107">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="2680f-108">Pobiera ICorDebugStepper — w celu wykonania operacji wykonywania krokowego względem to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2680f-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="2680f-109">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="2680f-110">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego czy wywołać tej ramki, lub zwraca wartość null, jeśli to jest najbardziej ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="2680f-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2680f-111">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="2680f-112">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego, która o nazwie tej ramki lub zwraca wartość null, jeśli to jest najbardziej zewnętrznego ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="2680f-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="2680f-113">GetChain, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="2680f-114">Pobiera wskaźnik do ICorDebugChain to `ICorDebugFrame` jest częścią.</span><span class="sxs-lookup"><span data-stu-id="2680f-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="2680f-115">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="2680f-116">Pobiera wskaźnik do ICorDebugCode skojarzone z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="2680f-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2680f-117">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="2680f-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="2680f-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2680f-119">GetFunctionToken, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="2680f-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="2680f-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="2680f-121">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="2680f-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="2680f-122">Pobiera adres bezwzględny zakres ramki stosu reprezentowany przez ten `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="2680f-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2680f-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2680f-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2680f-124">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="2680f-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2680f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2680f-125">Requirements</span></span>  
 <span data-ttu-id="2680f-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2680f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2680f-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2680f-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2680f-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2680f-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2680f-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2680f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2680f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2680f-130">See Also</span></span>  
 [<span data-ttu-id="2680f-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2680f-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
