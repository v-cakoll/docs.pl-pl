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
ms.openlocfilehash: aa06b7db6b7371e66853ed242f5e118fb5e5ff0c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096203"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="baf5f-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="baf5f-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="baf5f-103">Określa, czy określona ramka jest elementem nadrzędnym bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="baf5f-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baf5f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baf5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="baf5f-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="baf5f-106">podczas Wskaźnik do obiektu Frame, który chcesz oszacować dla stanu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="baf5f-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="baf5f-107">[out] `true`, jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="baf5f-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baf5f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="baf5f-108">Return Value</span></span>  
 <span data-ttu-id="baf5f-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="baf5f-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="baf5f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baf5f-110">HRESULT</span></span>|<span data-ttu-id="baf5f-111">Opis</span><span class="sxs-lookup"><span data-stu-id="baf5f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baf5f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="baf5f-112">S_OK</span></span>|<span data-ttu-id="baf5f-113">Stan nadrzędny został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="baf5f-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="baf5f-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="baf5f-114">E_FAIL</span></span>|<span data-ttu-id="baf5f-115">Nie można zwrócić stanu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="baf5f-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="baf5f-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="baf5f-116">E_INVALIDARG</span></span>|<span data-ttu-id="baf5f-117">`pPotentialParentFrame` lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="baf5f-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="baf5f-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="baf5f-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baf5f-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="baf5f-119">Remarks</span></span>  
 <span data-ttu-id="baf5f-120">`IsMatchingParentFrame` zwraca `true`, jeśli obiekt ramki przekazywany do metody jest elementem nadrzędnym obiektu ramki, na którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="baf5f-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="baf5f-121">Jeśli wywołasz metodę w ramce, która nie jest elementem podrzędnym określonej ramki, zwróci błąd.</span><span class="sxs-lookup"><span data-stu-id="baf5f-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baf5f-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="baf5f-122">Requirements</span></span>  
 <span data-ttu-id="baf5f-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baf5f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baf5f-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="baf5f-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="baf5f-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="baf5f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baf5f-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baf5f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf5f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baf5f-127">See also</span></span>

- [<span data-ttu-id="baf5f-128">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="baf5f-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="baf5f-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="baf5f-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="baf5f-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="baf5f-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
