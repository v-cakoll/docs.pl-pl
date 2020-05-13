---
title: ICorDebugRegisterSet::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: 04ae3c4dd663351eaf1a58646e24e8ae95aeb9ad
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378282"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a><span data-ttu-id="03309-102">ICorDebugRegisterSet::GetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="03309-102">ICorDebugRegisterSet::GetThreadContext Method</span></span>
<span data-ttu-id="03309-103">Pobiera kontekst bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="03309-103">Gets the context of the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03309-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="03309-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03309-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="03309-105">Parameters</span></span>  
 `contextSize`  
 <span data-ttu-id="03309-106">podczas Rozmiar tablicy w bajtach `context` .</span><span class="sxs-lookup"><span data-stu-id="03309-106">[in] The size, in bytes, of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="03309-107">[in. out] Tablica bajtów, która składa się ze `CONTEXT` struktury Win32 dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="03309-107">[in, out] An array of bytes that compose the Win32 `CONTEXT` structure for the current platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03309-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03309-108">Remarks</span></span>  
 <span data-ttu-id="03309-109">Debuger powinien wywołać tę funkcję zamiast `GetThreadContext` funkcji Win32, ponieważ wątek może być w stanie "przejęte", gdzie jego kontekst został tymczasowo zmieniony.</span><span class="sxs-lookup"><span data-stu-id="03309-109">The debugger should call this function instead of the Win32 `GetThreadContext` function, because the thread may be in a "hijacked" state where its context has been temporarily changed.</span></span> <span data-ttu-id="03309-110">Zwrócone dane są `CONTEXT` strukturą Win32 dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="03309-110">The data returned is a Win32 `CONTEXT` structure for the current platform.</span></span>  
  
 <span data-ttu-id="03309-111">W przypadku ramek spoza liścia klienci powinni sprawdzić, które rejestry są prawidłowe za pomocą [ICorDebugRegisterSet:: GetRegistersAvailable —](icordebugregisterset-getregistersavailable-method.md).</span><span class="sxs-lookup"><span data-stu-id="03309-111">For non-leaf frames, clients should check which registers are valid by using [ICorDebugRegisterSet::GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03309-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03309-112">Requirements</span></span>  
 <span data-ttu-id="03309-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03309-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03309-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03309-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03309-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="03309-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03309-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03309-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03309-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03309-117">See also</span></span>

- [<span data-ttu-id="03309-118">ICorDebugRegisterSet — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03309-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="03309-119">ICorDebugRegisterSet2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="03309-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
