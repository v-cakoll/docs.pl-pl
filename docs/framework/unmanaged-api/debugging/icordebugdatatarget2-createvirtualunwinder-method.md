---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 9fc4facda6253d0c68dcf89b2a1b06e639734efe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788856"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="90158-102">Metoda ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="90158-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="90158-103">Tworzy nowy wątek unwiatrer, który zaczyna odwracać od kontekstu początkowego (co nie musi być elementem liścia wątku).</span><span class="sxs-lookup"><span data-stu-id="90158-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90158-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90158-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="90158-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90158-105">Parameters</span></span>  
 <span data-ttu-id="90158-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="90158-106">nativeThreadID</span></span>  
 <span data-ttu-id="90158-107">podczas Identyfikator wątku natywnego wątku, którego stos ma być rozłożony.</span><span class="sxs-lookup"><span data-stu-id="90158-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="90158-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="90158-108">contextFlags</span></span>  
 <span data-ttu-id="90158-109">podczas Flagi określające, które części kontekstu są zdefiniowane w `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="90158-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="90158-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="90158-110">cbContext</span></span>  
 <span data-ttu-id="90158-111">podczas Rozmiar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="90158-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="90158-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="90158-112">initialContext</span></span>  
 <span data-ttu-id="90158-113">podczas Dane w kontekście.</span><span class="sxs-lookup"><span data-stu-id="90158-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="90158-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="90158-114">ppUnwinder</span></span>  
 <span data-ttu-id="90158-115">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="90158-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90158-116">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="90158-116">Return Value</span></span>  
 <span data-ttu-id="90158-117">`S_OK`, jeśli się to powiedzie.</span><span class="sxs-lookup"><span data-stu-id="90158-117">`S_OK` if successful.</span></span> <span data-ttu-id="90158-118">Wszystkie inne `HRESULT` wskazują niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="90158-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="90158-119">Wszystkie niepowodzenie `HRESULT` odebrane przez mscordbi są uznawane za krytyczne i powoduje, że metody [ICorDebug](icordebug-interface.md) zwracają `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="90158-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90158-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90158-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90158-121">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="90158-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90158-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90158-122">Requirements</span></span>  
 <span data-ttu-id="90158-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90158-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90158-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="90158-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90158-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="90158-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90158-126">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90158-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90158-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90158-127">See also</span></span>

- [<span data-ttu-id="90158-128">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="90158-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="90158-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="90158-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
