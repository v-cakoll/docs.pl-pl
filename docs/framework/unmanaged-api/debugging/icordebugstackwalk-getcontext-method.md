---
title: ICorDebugStackWalk::GetContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 743b0c8016ca5c0401046166a770d857215429a3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379218"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="8a851-102">ICorDebugStackWalk::GetContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a851-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="8a851-103">Zwraca kontekst dla bieżącej ramki w obiekcie [ICorDebugStackWalk](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8a851-103">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a851-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a851-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a851-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a851-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="8a851-106">podczas Flagi wskazujące żądaną zawartość buforu kontekstu (zdefiniowaną w WinNT. h).</span><span class="sxs-lookup"><span data-stu-id="8a851-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="8a851-107">podczas Przydzielony rozmiar buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8a851-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="8a851-108">określoną Rzeczywisty rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8a851-108">[out] The actual size of the context.</span></span> <span data-ttu-id="8a851-109">Ta wartość musi być mniejsza lub równa rozmiarowi buforu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8a851-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="8a851-110">określoną Bufor kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8a851-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a851-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8a851-111">Return Value</span></span>  
 <span data-ttu-id="8a851-112">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="8a851-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8a851-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a851-113">HRESULT</span></span>|<span data-ttu-id="8a851-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8a851-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a851-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a851-115">S_OK</span></span>|<span data-ttu-id="8a851-116">Kontekst dla bieżącej ramki został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="8a851-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="8a851-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a851-117">E_FAIL</span></span>|<span data-ttu-id="8a851-118">Nie można zwrócić kontekstu.</span><span class="sxs-lookup"><span data-stu-id="8a851-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="8a851-119">HRESULT_FROM_WIN32 (BUFOR ERROR_INSUFFICIENT)</span><span class="sxs-lookup"><span data-stu-id="8a851-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="8a851-120">Bufor kontekstu jest za mały.</span><span class="sxs-lookup"><span data-stu-id="8a851-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="8a851-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="8a851-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="8a851-122">Wskaźnik ramki znajduje się już na końcu stosu; w związku z tym nie można uzyskać dostępu do dodatkowych ramek.</span><span class="sxs-lookup"><span data-stu-id="8a851-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8a851-123">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8a851-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a851-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a851-124">Remarks</span></span>  
 <span data-ttu-id="8a851-125">Ponieważ rozwinięcia powoduje przywrócenie tylko podzbioru rejestrów, takich jak rejestry nietrwałe, kontekst może nie być dokładnie zgodny z stanem rejestru w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="8a851-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a851-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a851-126">Requirements</span></span>  
 <span data-ttu-id="8a851-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a851-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a851-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a851-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a851-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8a851-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a851-130">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a851-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a851-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a851-131">See also</span></span>

- [<span data-ttu-id="8a851-132">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8a851-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8a851-133">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8a851-133">Debugging</span></span>](index.md)
