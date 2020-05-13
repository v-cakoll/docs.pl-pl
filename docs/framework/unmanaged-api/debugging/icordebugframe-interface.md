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
ms.openlocfilehash: 9c2771d1338943406921447d96dd9a8748153a36
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209633"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="491e7-102">ICorDebugFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="491e7-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="491e7-103">Reprezentuje ramkę na bieżącym stosie.</span><span class="sxs-lookup"><span data-stu-id="491e7-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="491e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="491e7-104">Methods</span></span>  
  
|<span data-ttu-id="491e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-105">Method</span></span>|<span data-ttu-id="491e7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="491e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="491e7-107">CreateStepper — Metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="491e7-108">Pobiera ICorDebugStepper do wykonania operacji krokowe względem tego `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="491e7-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="491e7-109">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="491e7-110">Pobiera wskaźnik do elementu `ICorDebugFrame` w bieżącym łańcuchu, który ta ramka nazywa lub zwraca wartość null, jeśli jest to wewnętrzna ramka w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="491e7-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="491e7-111">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="491e7-112">Pobiera wskaźnik do elementu `ICorDebugFrame` w bieżącym łańcuchu, który wywołał tę ramkę, lub zwraca wartość null, jeśli jest to najbardziej skrajna ramka w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="491e7-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="491e7-113">GetChain, metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="491e7-114">Pobiera wskaźnik do ICorDebugChain, który `ICorDebugFrame` jest częścią.</span><span class="sxs-lookup"><span data-stu-id="491e7-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="491e7-115">GetCode, metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="491e7-116">Pobiera wskaźnik do ICorDebugCode skojarzonego z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="491e7-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="491e7-117">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="491e7-118">Pobiera wskaźnik do ICorDebugFunction, który zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="491e7-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="491e7-119">GetFunctionToken, metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="491e7-120">Pobiera token metadanych dla funkcji, która zawiera kod skojarzony z tą ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="491e7-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="491e7-121">GetStackRange — Metoda</span><span class="sxs-lookup"><span data-stu-id="491e7-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="491e7-122">Pobiera bezwzględny zakres adresów ramki stosu reprezentowanej przez ten element `ICorDebugFrame` .</span><span class="sxs-lookup"><span data-stu-id="491e7-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="491e7-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="491e7-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="491e7-124">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="491e7-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="491e7-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="491e7-125">Requirements</span></span>  
 <span data-ttu-id="491e7-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="491e7-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="491e7-127">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="491e7-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="491e7-128">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="491e7-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="491e7-129">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="491e7-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491e7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="491e7-130">See also</span></span>

- [<span data-ttu-id="491e7-131">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="491e7-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
