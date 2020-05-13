---
title: ICorDebugNativeFrame, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: dd87745a29514a2f9f05aa142baae4e05d4b4a7b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206600"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="82263-102">ICorDebugNativeFrame, interfejs</span><span class="sxs-lookup"><span data-stu-id="82263-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="82263-103">Wyspecjalizowana implementacja ICorDebugFrame używana w przypadku ramek natywnych.</span><span class="sxs-lookup"><span data-stu-id="82263-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82263-104">Metody</span><span class="sxs-lookup"><span data-stu-id="82263-104">Methods</span></span>  
  
|<span data-ttu-id="82263-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="82263-105">Method</span></span>|<span data-ttu-id="82263-106">Opis</span><span class="sxs-lookup"><span data-stu-id="82263-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="82263-107">CanSetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="82263-108">Pobiera wartość wskazującą, czy można bezpiecznie ustawić wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="82263-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="82263-109">GetIP, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="82263-110">Pobiera przesunięcie ramki stosu do kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="82263-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="82263-111">GetLocalDoubleRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="82263-112">Pobiera wskaźnik do elementu ICorDebugValue, który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w dwóch rejestrach pamięci ramki natywnej.</span><span class="sxs-lookup"><span data-stu-id="82263-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="82263-113">GetLocalMemoryRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="82263-114">Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której niskie bity są przechowywane w określonym rejestrze, a duże bity są przechowywane w określonym adresie pamięci.</span><span class="sxs-lookup"><span data-stu-id="82263-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="82263-115">GetLocalMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="82263-116">Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej przechowywanej w określonym adresie pamięci.</span><span class="sxs-lookup"><span data-stu-id="82263-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="82263-117">GetLocalRegisterMemoryValue, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="82263-118">Pobiera wskaźnik do obiektu `ICorDebugValue` , który reprezentuje wartość zmiennej lokalnej, w której duże bity są przechowywane w określonym rejestrze, a niskie bity są przechowywane w określonym adresie pamięci</span><span class="sxs-lookup"><span data-stu-id="82263-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="82263-119">GetLocalRegisterValue, metoda</span><span class="sxs-lookup"><span data-stu-id="82263-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="82263-120">Pobiera wskaźnik do elementu `ICorDebugValue` , który reprezentuje wartość argumentu lub zmiennej lokalnej przechowywanej w określonym rejestrze macierzystym.</span><span class="sxs-lookup"><span data-stu-id="82263-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="82263-121">GetRegisterSet — Metoda</span><span class="sxs-lookup"><span data-stu-id="82263-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="82263-122">Pobiera wskaźnik do elementu [ICorDebugRegisterSet](icordebugregisterset-interface.md) , który reprezentuje zestaw rejestru dla tego elementu `ICorDebugNativeFrame` .</span><span class="sxs-lookup"><span data-stu-id="82263-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="82263-123">SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="82263-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="82263-124">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="82263-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82263-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82263-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82263-126">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="82263-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82263-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="82263-127">Requirements</span></span>  
 <span data-ttu-id="82263-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82263-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82263-129">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="82263-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82263-130">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="82263-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82263-131">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82263-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82263-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82263-132">See also</span></span>

- [<span data-ttu-id="82263-133">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="82263-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
