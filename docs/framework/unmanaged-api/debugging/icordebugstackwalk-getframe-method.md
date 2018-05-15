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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 548a8a7743c02be5734b677010627f847c5bc4b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="c653f-102">ICorDebugStackWalk::GetFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="c653f-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="c653f-103">Pobiera bieżącą ramkę w [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="c653f-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c653f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c653f-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c653f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c653f-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="c653f-106">[in] Wskaźnik do adresu obiekt utworzony ramki, który reprezentuje bieżącej ramki stosu.</span><span class="sxs-lookup"><span data-stu-id="c653f-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c653f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c653f-107">Return Value</span></span>  
 <span data-ttu-id="c653f-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="c653f-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c653f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c653f-109">HRESULT</span></span>|<span data-ttu-id="c653f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="c653f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c653f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c653f-111">S_OK</span></span>|<span data-ttu-id="c653f-112">Środowisko uruchomieniowe pomyślnie zwrócono bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="c653f-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="c653f-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c653f-113">E_FAIL</span></span>|<span data-ttu-id="c653f-114">Nie zwrócono bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="c653f-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="c653f-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c653f-115">S_FALSE</span></span>|<span data-ttu-id="c653f-116">Bieżącej ramki jest ramka stosu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="c653f-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="c653f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c653f-117">E_INVALIDARG</span></span>|<span data-ttu-id="c653f-118">`pFrame` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="c653f-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="c653f-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="c653f-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="c653f-120">Wskaźnik ramki już znajduje się na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.</span><span class="sxs-lookup"><span data-stu-id="c653f-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="c653f-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c653f-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c653f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c653f-122">Remarks</span></span>  
 <span data-ttu-id="c653f-123">`ICorDebugStackWalk` Zwraca tylko ramek stosu rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="c653f-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="c653f-124">Użyj [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metodę, aby zwrócić wewnętrzny ramki.</span><span class="sxs-lookup"><span data-stu-id="c653f-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="c653f-125">(Wewnętrzny ramki są wypychana na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych struktur danych).</span><span class="sxs-lookup"><span data-stu-id="c653f-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c653f-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c653f-126">Requirements</span></span>  
 <span data-ttu-id="c653f-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c653f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c653f-128">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c653f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c653f-129">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c653f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c653f-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c653f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c653f-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c653f-131">See Also</span></span>  
 [<span data-ttu-id="c653f-132">ICorDebugStackWalk, interfejs</span><span class="sxs-lookup"><span data-stu-id="c653f-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="c653f-133">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c653f-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c653f-134">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="c653f-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
