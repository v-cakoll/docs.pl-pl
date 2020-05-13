---
title: ICorDebugStackWalk::GetFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
ms.openlocfilehash: 5f80125a67e634dda05b9427b5f46db8f21b29f8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379198"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="8763a-102">ICorDebugStackWalk::GetFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="8763a-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="8763a-103">Pobiera bieżącą ramkę w obiekcie [ICorDebugStackWalk](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="8763a-103">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8763a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8763a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8763a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8763a-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="8763a-106">podczas Wskaźnik do adresu utworzonego obiektu Frame, który reprezentuje bieżącą ramkę w stosie.</span><span class="sxs-lookup"><span data-stu-id="8763a-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8763a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8763a-107">Return Value</span></span>  
 <span data-ttu-id="8763a-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="8763a-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8763a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8763a-109">HRESULT</span></span>|<span data-ttu-id="8763a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8763a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8763a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8763a-111">S_OK</span></span>|<span data-ttu-id="8763a-112">Środowisko uruchomieniowe pomyślnie zwróciło bieżącą ramkę.</span><span class="sxs-lookup"><span data-stu-id="8763a-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="8763a-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8763a-113">E_FAIL</span></span>|<span data-ttu-id="8763a-114">Bieżąca ramka nie została zwrócona.</span><span class="sxs-lookup"><span data-stu-id="8763a-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="8763a-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8763a-115">S_FALSE</span></span>|<span data-ttu-id="8763a-116">Bieżąca ramka jest natywną ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="8763a-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="8763a-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8763a-117">E_INVALIDARG</span></span>|<span data-ttu-id="8763a-118">`pFrame`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="8763a-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="8763a-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="8763a-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="8763a-120">Wskaźnik ramki znajduje się już na końcu stosu; w związku z tym nie można uzyskać dostępu do dodatkowych ramek.</span><span class="sxs-lookup"><span data-stu-id="8763a-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8763a-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="8763a-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8763a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8763a-122">Remarks</span></span>  
 <span data-ttu-id="8763a-123">`ICorDebugStackWalk`zwraca tylko rzeczywiste ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="8763a-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="8763a-124">Użyj metody [ICorDebugThread3:: GetActiveInternalFrames —](icordebugthread3-getactiveinternalframes-method.md) , aby zwrócić ramki wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="8763a-124">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="8763a-125">(Ramki wewnętrzne to struktury danych wypychane na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych).</span><span class="sxs-lookup"><span data-stu-id="8763a-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8763a-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8763a-126">Requirements</span></span>  
 <span data-ttu-id="8763a-127">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8763a-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8763a-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8763a-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8763a-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8763a-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8763a-130">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8763a-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8763a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8763a-131">See also</span></span>

- [<span data-ttu-id="8763a-132">ICorDebugStackWalk — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8763a-132">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="8763a-133">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8763a-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8763a-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8763a-134">Debugging</span></span>](index.md)
