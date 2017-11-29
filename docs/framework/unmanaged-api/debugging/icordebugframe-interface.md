---
title: ICorDebugFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFrame
helpviewer_keywords: ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2acc825f6592eae80f67e7614ca45f175b6756d8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugframe-interface1"></a><span data-ttu-id="38587-102">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="38587-102">ICorDebugFrame Interface1</span></span>
<span data-ttu-id="38587-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="38587-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38587-104">Metody</span><span class="sxs-lookup"><span data-stu-id="38587-104">Methods</span></span>  
  
|<span data-ttu-id="38587-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="38587-105">Method</span></span>|<span data-ttu-id="38587-106">Opis</span><span class="sxs-lookup"><span data-stu-id="38587-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38587-107">CreateStepper — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="38587-108">Pobiera ICorDebugStepper — w celu wykonania operacji wykonywania krokowego względem to `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="38587-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="38587-109">GetCallee — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="38587-110">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego czy wywołać tej ramki, lub zwraca wartość null, jeśli to jest najbardziej ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="38587-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="38587-111">GetCaller — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="38587-112">Pobiera wskaźnik do `ICorDebugFrame` w łańcuchu bieżącego, która o nazwie tej ramki lub zwraca wartość null, jeśli to jest najbardziej zewnętrznego ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="38587-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="38587-113">GetChain — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="38587-114">Pobiera wskaźnik do ICorDebugChain to `ICorDebugFrame` jest częścią.</span><span class="sxs-lookup"><span data-stu-id="38587-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="38587-115">GetCode — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="38587-116">Pobiera wskaźnik do ICorDebugCode skojarzone z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="38587-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="38587-117">GetFunction — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="38587-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="38587-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="38587-119">GetFunctionToken — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="38587-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="38587-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="38587-121">GetStackRange — metoda</span><span class="sxs-lookup"><span data-stu-id="38587-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="38587-122">Pobiera adres bezwzględny zakres ramki stosu reprezentowany przez ten `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="38587-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38587-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38587-123">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38587-124">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="38587-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38587-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38587-125">Requirements</span></span>  
 <span data-ttu-id="38587-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38587-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38587-127">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38587-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38587-128">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38587-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38587-129">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38587-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38587-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38587-130">See Also</span></span>  
 [<span data-ttu-id="38587-131">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="38587-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
