---
title: ICorDebugNativeFrame::SetIP — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.SetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::SetIP
helpviewer_keywords:
- ICorDebugNativeFrame::SetIP method [.NET Framework debugging]
- SetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 57784a51-c76d-48f8-9392-584d0e1946d9
topic_type:
- apiref
ms.openlocfilehash: 786c0e7b38c74fd02dd6f7536af1899f295b0305
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206445"
---
# <a name="icordebugnativeframesetip-method"></a><span data-ttu-id="ecf0a-102">ICorDebugNativeFrame::SetIP — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecf0a-102">ICorDebugNativeFrame::SetIP Method</span></span>
<span data-ttu-id="ecf0a-103">Ustawia wskaźnik instrukcji na określoną lokalizację przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-103">Sets the instruction pointer to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecf0a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecf0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecf0a-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="ecf0a-106">podczas Lokalizacja przesunięcia w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-106">[in] The offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecf0a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecf0a-107">Remarks</span></span>  
 <span data-ttu-id="ecf0a-108">Wywołuje `SetIP` natychmiastowe unieważnienie wszystkich ramek i łańcuchów dla bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-108">Calls to `SetIP` immediately invalidate all frames and chains for the current thread.</span></span> <span data-ttu-id="ecf0a-109">Jeśli debuger wymaga informacji o klatce po wywołaniu `SetIP` , musi wykonać nowy ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-109">If the debugger needs frame information after a call to `SetIP`, it must perform a new stack trace.</span></span>  
  
 <span data-ttu-id="ecf0a-110">[ICorDebug](icordebug-interface.md) spróbuje zachować prawidłowy stan ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-110">[ICorDebug](icordebug-interface.md) will attempt to keep the stack frame in a valid state.</span></span> <span data-ttu-id="ecf0a-111">Jednak nawet jeśli ramka jest w prawidłowym stanie, o ile jest to związane ze środowiskiem uruchomieniowym, nadal mogą wystąpić problemy, takie jak Niezainicjowane zmienne lokalne itd.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-111">However, even if the frame is in a valid state, as far as the runtime is concerned, there still may be problems, such as uninitialized local variables, and so on.</span></span> <span data-ttu-id="ecf0a-112">Obiekt wywołujący jest odpowiedzialny za ubezpieczenie spójność uruchomionego programu.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-112">The caller is responsible for insuring coherency of the running program.</span></span>  
  
 <span data-ttu-id="ecf0a-113">Na platformach 64-bitowych wskaźnik instrukcji nie może zostać przeniesiony z `catch` `finally` bloku lub.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-113">On 64-bit platforms, the instruction pointer cannot be moved out of a `catch` or `finally` block.</span></span> <span data-ttu-id="ecf0a-114">Jeśli `SetIP` jest wywoływana w celu przechodzenia na platformę 64-bitową, zwróci wynik HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="ecf0a-114">If `SetIP` is called to make such a move on a 64-bit platform, it will return an HRESULT indicating failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecf0a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecf0a-115">Requirements</span></span>  
 <span data-ttu-id="ecf0a-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecf0a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf0a-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ecf0a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecf0a-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecf0a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecf0a-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf0a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ecf0a-120">See also</span></span>
