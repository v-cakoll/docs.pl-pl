---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 7a479fba9bbcf28c60474fffc6219af23e62c251
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976502"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="8b1f3-102">Metoda ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="8b1f3-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="8b1f3-103">Tworzy nowy wątek unwiatrer, który zaczyna odwracać od kontekstu początkowego (co nie musi być elementem liścia wątku).</span><span class="sxs-lookup"><span data-stu-id="8b1f3-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b1f3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b1f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b1f3-105">Parameters</span></span>  
 <span data-ttu-id="8b1f3-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="8b1f3-106">nativeThreadID</span></span>  
 <span data-ttu-id="8b1f3-107">podczas Identyfikator wątku natywnego wątku, którego stos ma być rozłożony.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="8b1f3-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="8b1f3-108">contextFlags</span></span>  
 <span data-ttu-id="8b1f3-109">podczas Flagi określające, w `initialContext`których częściach kontekstu są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="8b1f3-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="8b1f3-110">cbContext</span></span>  
 <span data-ttu-id="8b1f3-111">podczas Rozmiar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="8b1f3-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="8b1f3-112">initialContext</span></span>  
 <span data-ttu-id="8b1f3-113">podczas Dane w kontekście.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="8b1f3-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="8b1f3-114">ppUnwinder</span></span>  
 <span data-ttu-id="8b1f3-115">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b1f3-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8b1f3-116">Return Value</span></span>  
 <span data-ttu-id="8b1f3-117">`S_OK`w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-117">`S_OK` if successful.</span></span> <span data-ttu-id="8b1f3-118">Wszystkie inne `HRESULT` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="8b1f3-119">Wszystkie błędy `HRESULT` odebrane przez mscordbi są uznawane za krytyczne [ICorDebug](icordebug-interface.md) i powodują zwrócenie `CORDBG_E_DATA_TARGET_ERROR`metod ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b1f3-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b1f3-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b1f3-121">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8b1f3-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b1f3-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b1f3-122">Requirements</span></span>  
 <span data-ttu-id="8b1f3-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b1f3-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b1f3-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b1f3-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b1f3-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8b1f3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b1f3-126">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b1f3-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1f3-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b1f3-127">See also</span></span>

- [<span data-ttu-id="8b1f3-128">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="8b1f3-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="8b1f3-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8b1f3-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
