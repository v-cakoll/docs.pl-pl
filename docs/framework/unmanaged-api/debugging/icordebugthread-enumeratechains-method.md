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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caeb60c33580f7171a6959c3046cf7312868851b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="ae9da-102">ICorDebugThread::EnumerateChains — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae9da-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="ae9da-103">Pobiera wskaźnika interfejsu, aby moduł wyliczający ICorDebugChainEnum, który zawiera wszystkie łańcuchy stosu w tym obiekcie ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ae9da-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae9da-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae9da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae9da-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="ae9da-106">[out] Wskaźnik do adresu `ICorDebugChainEnum` powiązany obiekt, który umożliwia wyliczenie wszystkich stosu, w tym wątku, zaczynając od łańcucha aktywny (to znaczy najnowszej).</span><span class="sxs-lookup"><span data-stu-id="ae9da-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae9da-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae9da-107">Remarks</span></span>  
 <span data-ttu-id="ae9da-108">Łańcuch stosu reprezentuje stosu wywołań fizycznych wątku.</span><span class="sxs-lookup"><span data-stu-id="ae9da-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="ae9da-109">Następujące okoliczności Utwórz granicę łańcucha stosu:</span><span class="sxs-lookup"><span data-stu-id="ae9da-109">The following circumstances create a stack chain boundary:</span></span>  
  
-   <span data-ttu-id="ae9da-110">Przejście niezarządzany zarządzany lub niezarządzany zarządzany.</span><span class="sxs-lookup"><span data-stu-id="ae9da-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
-   <span data-ttu-id="ae9da-111">Przełączenie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="ae9da-111">A context switch.</span></span>  
  
-   <span data-ttu-id="ae9da-112">A debugera przejęcie kontroli nad wątku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ae9da-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="ae9da-113">W przypadku prostego dla wątku, który działa wyłącznie zarządzany kod w pojedynczym kontekście odpowiednika będą istnieć między wątków i łańcuchów stosu.</span><span class="sxs-lookup"><span data-stu-id="ae9da-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="ae9da-114">Debuger może być rozmieszczanie stosy wywołań fizycznych, wszystkich wątków w stosy wywołań logiczne.</span><span class="sxs-lookup"><span data-stu-id="ae9da-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="ae9da-115">Wymagałoby to sortowanie łańcuchów wszystkie wątki według ich relacje wywołujący/wywoływany i zgrupowania je.</span><span class="sxs-lookup"><span data-stu-id="ae9da-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae9da-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae9da-116">Requirements</span></span>  
 <span data-ttu-id="ae9da-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae9da-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae9da-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae9da-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae9da-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae9da-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae9da-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae9da-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
