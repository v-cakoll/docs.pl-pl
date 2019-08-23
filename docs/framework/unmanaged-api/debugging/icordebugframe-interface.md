---
title: ICorDebugFrame, interfejs
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
ms.openlocfilehash: d4744ea67d0ce0d9ad2b13c45bdef65f884ef925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937005"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="ae5a4-102">ICorDebugFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="ae5a4-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="ae5a4-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae5a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ae5a4-104">Methods</span></span>  
  
|<span data-ttu-id="ae5a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-105">Method</span></span>|<span data-ttu-id="ae5a4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ae5a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae5a4-107">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="ae5a4-108">Pobiera ICorDebugStepper do wykonania operacji krokowe względem tego `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="ae5a4-109">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="ae5a4-110">Pobiera wskaźnik do `ICorDebugFrame` elementu w bieżącym łańcuchu, który ta ramka nazywa lub zwraca wartość null, jeśli jest to wewnętrzna ramka w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="ae5a4-111">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="ae5a4-112">Pobiera wskaźnik do `ICorDebugFrame` elementu w bieżącym łańcuchu, który wywołał tę ramkę, lub zwraca wartość null, jeśli jest to najbardziej skrajna ramka w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="ae5a4-113">GetChain, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="ae5a4-114">Pobiera wskaźnik do ICorDebugChain `ICorDebugFrame` , który jest częścią.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="ae5a4-115">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="ae5a4-116">Pobiera wskaźnik do ICorDebugCode skojarzonego z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="ae5a4-117">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="ae5a4-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="ae5a4-119">GetFunctionToken, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="ae5a4-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="ae5a4-121">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="ae5a4-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="ae5a4-122">Pobiera bezwzględny zakres adresów ramki stosu reprezentowanej przez ten `ICorDebugFrame`element.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae5a4-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae5a4-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae5a4-124">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="ae5a4-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae5a4-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae5a4-125">Requirements</span></span>  
 <span data-ttu-id="ae5a4-126">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae5a4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5a4-127">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae5a4-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae5a4-128">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae5a4-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae5a4-129">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5a4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5a4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae5a4-130">See also</span></span>

- [<span data-ttu-id="ae5a4-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ae5a4-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
