---
title: ICorDebugThread::EnumerateChains — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.EnumerateChains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::EnumerateChains
helpviewer_keywords:
- EnumerateChains method [.NET Framework debugging]
- ICorDebugThread::EnumerateChains method [.NET Framework debugging]
ms.assetid: ec00bc21-117e-4acd-9301-2cfafd5be8d3
topic_type:
- apiref
ms.openlocfilehash: 38fe50f5a6608bb27d7a7818dee4784a7f8113ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133608"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="d4d44-102">ICorDebugThread::EnumerateChains — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4d44-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="d4d44-103">Pobiera wskaźnik interfejsu do modułu wyliczającego ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym obiekcie ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d4d44-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d44-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4d44-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4d44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4d44-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="d4d44-106">określoną Wskaźnik do adresu obiektu `ICorDebugChainEnum`, który umożliwia wyliczenie wszystkich łańcuchów stosu w tym wątku, rozpoczynając od aktywnego (czyli ostatniego) łańcucha.</span><span class="sxs-lookup"><span data-stu-id="d4d44-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4d44-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4d44-107">Remarks</span></span>  
 <span data-ttu-id="d4d44-108">Łańcuch stosu reprezentuje stos wywołań fizycznych wątku.</span><span class="sxs-lookup"><span data-stu-id="d4d44-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="d4d44-109">W następujących sytuacjach należy utworzyć granicę łańcucha stosu:</span><span class="sxs-lookup"><span data-stu-id="d4d44-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="d4d44-110">Przejście z zarządzanego lub niezarządzanego lub niezarządzanego do zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d4d44-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="d4d44-111">Przełącznik kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d4d44-111">A context switch.</span></span>  
  
- <span data-ttu-id="d4d44-112">Debuger przejmowanie wątku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d4d44-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="d4d44-113">W prostym przypadku wątku, w którym działa kod zarządzany całkowicie w pojedynczym kontekście, między wątkami i łańcuchami stosu będzie nadana korespondencja typu jeden do jednego.</span><span class="sxs-lookup"><span data-stu-id="d4d44-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="d4d44-114">Debuger może chcieć zmienić rozmieszczenie stosów wywołań fizycznych wszystkich wątków na stosy wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="d4d44-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="d4d44-115">Obejmuje to posortowanie wszystkich łańcuchów wątków według ich relacji wywołujących/wywoływanych i przegrupowanie ich.</span><span class="sxs-lookup"><span data-stu-id="d4d44-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d44-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4d44-116">Requirements</span></span>  
 <span data-ttu-id="d4d44-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d44-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d44-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d4d44-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4d44-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d4d44-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4d44-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d44-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
