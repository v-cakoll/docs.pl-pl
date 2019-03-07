---
title: ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56d2c28529d3f3ee87fe3fdedd91634133ebf864
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492208"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="e126d-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="e126d-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="e126d-103">Określa, czy ramki o określonym nadrzędny bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="e126d-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e126d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e126d-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e126d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e126d-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="e126d-106">[in] Wskaźnik do obiektu ramki, który chcesz ocenić, czy stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e126d-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="e126d-107">[out] `true` Jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e126d-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e126d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e126d-108">Return Value</span></span>  
 <span data-ttu-id="e126d-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e126d-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e126d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e126d-110">HRESULT</span></span>|<span data-ttu-id="e126d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e126d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e126d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e126d-112">S_OK</span></span>|<span data-ttu-id="e126d-113">Stan nadrzędnej została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="e126d-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="e126d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e126d-114">E_FAIL</span></span>|<span data-ttu-id="e126d-115">Nie można zwrócić stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e126d-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="e126d-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e126d-116">E_INVALIDARG</span></span>|<span data-ttu-id="e126d-117">`pPotentialParentFrame` lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="e126d-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e126d-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="e126d-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e126d-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e126d-119">Remarks</span></span>  
 <span data-ttu-id="e126d-120">`IsMatchingParentFrame` Zwraca `true` Jeśli obiekt w ramce przekazać do metody jest elementem nadrzędnym wywołaniu metody obiekt w ramce.</span><span class="sxs-lookup"><span data-stu-id="e126d-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="e126d-121">Jeśli wywołasz metodę dla ramki, który nie jest elementem podrzędnym ramki o określonym zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="e126d-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e126d-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e126d-122">Requirements</span></span>  
 <span data-ttu-id="e126d-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e126d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e126d-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e126d-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e126d-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e126d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e126d-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e126d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e126d-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e126d-127">See also</span></span>
- [<span data-ttu-id="e126d-128">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e126d-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="e126d-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e126d-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e126d-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e126d-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
