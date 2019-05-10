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
ms.openlocfilehash: f131f7566376d6474f3189d5eb612b30bec2e2b7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648436"
---
# <a name="icordebugthreadenumeratechains-method"></a><span data-ttu-id="5aab6-102">ICorDebugThread::EnumerateChains — Metoda</span><span class="sxs-lookup"><span data-stu-id="5aab6-102">ICorDebugThread::EnumerateChains Method</span></span>
<span data-ttu-id="5aab6-103">Pobiera moduł wyliczający icordebugchainenum —, który zawiera wszystkie łańcuchów stosu, w tym obiekcie ICorDebugThread wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5aab6-103">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5aab6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5aab6-104">Syntax</span></span>  
  
```  
HRESULT EnumerateChains (  
    [out] ICorDebugChainEnum **ppChains  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5aab6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5aab6-105">Parameters</span></span>  
 `ppChains`  
 <span data-ttu-id="5aab6-106">[out] Wskaźnik na adres `ICorDebugChainEnum` obiekt, który umożliwia wyliczenie wszystkich stosu, który tworzy powiązanie w tym wątku, zaczynając od łańcucha aktywny (to znaczy najnowszej).</span><span class="sxs-lookup"><span data-stu-id="5aab6-106">[out] A pointer to the address of an `ICorDebugChainEnum` object that allows enumeration of all the stack chains in this thread, starting at the active (that is, the most recent) chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5aab6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5aab6-107">Remarks</span></span>  
 <span data-ttu-id="5aab6-108">Łańcuch stosu reprezentuje stosu wywołań fizycznych dla wątku.</span><span class="sxs-lookup"><span data-stu-id="5aab6-108">The stack chain represents the physical call stack for the thread.</span></span> <span data-ttu-id="5aab6-109">Następujące okoliczności Utwórz granicę łańcucha stosu:</span><span class="sxs-lookup"><span data-stu-id="5aab6-109">The following circumstances create a stack chain boundary:</span></span>  
  
- <span data-ttu-id="5aab6-110">Zarządzane do niezarządzanego lub niezarządzane do zarządzanego przejście.</span><span class="sxs-lookup"><span data-stu-id="5aab6-110">A managed-to-unmanaged or unmanaged-to-managed transition.</span></span>  
  
- <span data-ttu-id="5aab6-111">Przełączenie kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5aab6-111">A context switch.</span></span>  
  
- <span data-ttu-id="5aab6-112">A debugera przejęcie kontroli nad wątku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5aab6-112">A debugger hijacking of a user thread.</span></span>  
  
 <span data-ttu-id="5aab6-113">W prostym przypadku wątku, który działa wyłącznie zarządzany kod w jednym kontekście odpowiednika będzie istnieć między wątkami i łańcuchów stosu.</span><span class="sxs-lookup"><span data-stu-id="5aab6-113">In the simple case for a thread that is running purely managed code in a single context, a one-to-one correspondence will exist between threads and stack chains.</span></span>  
  
 <span data-ttu-id="5aab6-114">Debuger może być ponowne rozmieszczanie stosy wywołań fizycznych wszystkich wątków do stosów wywołań logicznych.</span><span class="sxs-lookup"><span data-stu-id="5aab6-114">A debugger may want to rearrange the physical call stacks of all threads into logical call stacks.</span></span> <span data-ttu-id="5aab6-115">Wymagałoby to sortowanie łańcuchów wszystkie wątki według ich relacji wywołujący/wywoływany i zgrupowania je.</span><span class="sxs-lookup"><span data-stu-id="5aab6-115">This would involve sorting all the threads' chains by their caller/callee relationships and regrouping them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aab6-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5aab6-116">Requirements</span></span>  
 <span data-ttu-id="5aab6-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aab6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aab6-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5aab6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aab6-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5aab6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aab6-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aab6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
