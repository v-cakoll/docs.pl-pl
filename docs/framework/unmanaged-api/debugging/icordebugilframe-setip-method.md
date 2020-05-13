---
title: ICorDebugILFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type:
- apiref
ms.openlocfilehash: 325b2a009e77d87e95bdb02803dd3c4675c26ddc
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213429"
---
# <a name="icordebugilframesetip-method"></a><span data-ttu-id="74977-102">ICorDebugILFrame::SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="74977-102">ICorDebugILFrame::SetIP Method</span></span>
<span data-ttu-id="74977-103">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="74977-103">Sets the instruction pointer to the specified offset location in the Microsoft intermediate language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74977-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74977-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74977-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74977-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="74977-106">Lokalizacja przesunięcia w kodzie MSIL.</span><span class="sxs-lookup"><span data-stu-id="74977-106">The offset location in the MSIL code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74977-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74977-107">Remarks</span></span>  
 <span data-ttu-id="74977-108">Wywołuje `SetIP` natychmiastowe unieważnienie wszystkich ramek i łańcuchów dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="74977-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="74977-109">Jeśli debuger wymaga informacji o klatce po wywołaniu `SetIP` , musi wykonać nowy ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="74977-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="74977-110">[ICorDebug](icordebug-interface.md) spróbuje zachować prawidłowy stan ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="74977-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="74977-111">Jednak nawet jeśli ramka jest w prawidłowym stanie, nadal mogą wystąpić problemy, takie jak Niezainicjowane zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="74977-111">However, even if the frame is in a valid state, there still may be problems such as uninitialized local variables.</span></span> <span data-ttu-id="74977-112">Obiekt wywołujący jest odpowiedzialny za zapewnienie spójność uruchomionego programu.</span><span class="sxs-lookup"><span data-stu-id="74977-112">The caller is responsible for ensuring the coherency of the running program.</span></span>  
  
 <span data-ttu-id="74977-113">Na platformach 64-bitowych wskaźnik instrukcji nie może zostać przeniesiony z `catch` `finally` bloku lub.</span><span class="sxs-lookup"><span data-stu-id="74977-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="74977-114">Jeśli `SetIP` jest wywoływana w celu przechodzenia na platformę 64-bitową, zwróci wynik HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="74977-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74977-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74977-115">Requirements</span></span>  
 <span data-ttu-id="74977-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74977-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74977-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74977-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74977-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74977-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74977-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74977-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
