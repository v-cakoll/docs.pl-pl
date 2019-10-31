---
title: ICorDebugFrame — Interfejs
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
ms.openlocfilehash: 5aeea11b7e61869968aafe3425e27d6004f495ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124071"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="4473e-102">ICorDebugFrame — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4473e-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="4473e-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="4473e-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4473e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4473e-104">Methods</span></span>  
  
|<span data-ttu-id="4473e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-105">Method</span></span>|<span data-ttu-id="4473e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4473e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4473e-107">CreateStepper, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-107">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-createstepper-method.md)|<span data-ttu-id="4473e-108">Pobiera ICorDebugStepper do wykonania operacji wykonywania krokowego względem tego `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="4473e-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="4473e-109">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-109">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcallee-method.md)|<span data-ttu-id="4473e-110">Pobiera wskaźnik do `ICorDebugFrame` w bieżącym łańcuchu, który ta ramka nazywa lub zwraca wartość null, jeśli jest to wewnętrzna ramka w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="4473e-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="4473e-111">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-111">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcaller-method.md)|<span data-ttu-id="4473e-112">Pobiera wskaźnik do `ICorDebugFrame` w bieżącym łańcuchu, który wywołał tę ramkę, lub zwraca wartość null, jeśli jest to najbardziej skrajna ramka w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="4473e-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="4473e-113">GetChain, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-113">GetChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getchain-method.md)|<span data-ttu-id="4473e-114">Pobiera wskaźnik do ICorDebugChain, do którego należy ten `ICorDebugFrame` jest częścią.</span><span class="sxs-lookup"><span data-stu-id="4473e-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="4473e-115">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-115">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)|<span data-ttu-id="4473e-116">Pobiera wskaźnik do ICorDebugCode skojarzonego z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="4473e-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="4473e-117">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-117">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunction-method.md)|<span data-ttu-id="4473e-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="4473e-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="4473e-119">GetFunctionToken, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-119">GetFunctionToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="4473e-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="4473e-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="4473e-121">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="4473e-121">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getstackrange-method.md)|<span data-ttu-id="4473e-122">Pobiera bezwzględny zakres adresów ramki stosu reprezentowanej przez ten `ICorDebugFrame`.</span><span class="sxs-lookup"><span data-stu-id="4473e-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4473e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4473e-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4473e-124">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="4473e-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4473e-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4473e-125">Requirements</span></span>  
 <span data-ttu-id="4473e-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4473e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4473e-127">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4473e-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4473e-128">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4473e-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4473e-129">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4473e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4473e-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4473e-130">See also</span></span>

- [<span data-ttu-id="4473e-131">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4473e-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
