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
ms.openlocfilehash: 89576e2b3d5fb4df0cccfdd28c80a5cb67331597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791897"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="d71df-102">ICorDebugStackWalk::GetFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="d71df-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="d71df-103">Pobiera bieżącą ramkę w obiekcie [ICorDebugStackWalk](icordebugstackwalk-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d71df-103">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d71df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d71df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d71df-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="d71df-106">podczas Wskaźnik do adresu utworzonego obiektu Frame, który reprezentuje bieżącą ramkę w stosie.</span><span class="sxs-lookup"><span data-stu-id="d71df-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d71df-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d71df-107">Return Value</span></span>  
 <span data-ttu-id="d71df-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d71df-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d71df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d71df-109">HRESULT</span></span>|<span data-ttu-id="d71df-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d71df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d71df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d71df-111">S_OK</span></span>|<span data-ttu-id="d71df-112">Środowisko uruchomieniowe pomyślnie zwróciło bieżącą ramkę.</span><span class="sxs-lookup"><span data-stu-id="d71df-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="d71df-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d71df-113">E_FAIL</span></span>|<span data-ttu-id="d71df-114">Bieżąca ramka nie została zwrócona.</span><span class="sxs-lookup"><span data-stu-id="d71df-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="d71df-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d71df-115">S_FALSE</span></span>|<span data-ttu-id="d71df-116">Bieżąca ramka jest natywną ramką stosu.</span><span class="sxs-lookup"><span data-stu-id="d71df-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="d71df-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d71df-117">E_INVALIDARG</span></span>|<span data-ttu-id="d71df-118">Parametr `pFrame` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d71df-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="d71df-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="d71df-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="d71df-120">Wskaźnik ramki znajduje się już na końcu stosu; w związku z tym nie można uzyskać dostępu do dodatkowych ramek.</span><span class="sxs-lookup"><span data-stu-id="d71df-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d71df-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d71df-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d71df-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d71df-122">Remarks</span></span>  
 <span data-ttu-id="d71df-123">`ICorDebugStackWalk` zwraca tylko rzeczywiste ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="d71df-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="d71df-124">Użyj metody [ICorDebugThread3:: GetActiveInternalFrames —](icordebugthread3-getactiveinternalframes-method.md) , aby zwrócić ramki wewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="d71df-124">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="d71df-125">(Ramki wewnętrzne to struktury danych wypychane na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych).</span><span class="sxs-lookup"><span data-stu-id="d71df-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71df-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d71df-126">Requirements</span></span>  
 <span data-ttu-id="d71df-127">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d71df-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71df-128">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d71df-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d71df-129">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d71df-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d71df-130">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d71df-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71df-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d71df-131">See also</span></span>

- [<span data-ttu-id="d71df-132">ICorDebugStackWalk, interfejs</span><span class="sxs-lookup"><span data-stu-id="d71df-132">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="d71df-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d71df-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d71df-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d71df-134">Debugging</span></span>](index.md)
