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
ms.openlocfilehash: 5bcced647af6436bd8f5b1f3779d9368b6173d11
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213039"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="baaec-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="baaec-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="baaec-103">Określa, czy określona ramka jest elementem nadrzędnym bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="baaec-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baaec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="baaec-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baaec-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="baaec-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="baaec-106">podczas Wskaźnik do obiektu Frame, który chcesz oszacować dla stanu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="baaec-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="baaec-107">[out] `true` Jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="baaec-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="baaec-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="baaec-108">Return Value</span></span>  
 <span data-ttu-id="baaec-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="baaec-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="baaec-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="baaec-110">HRESULT</span></span>|<span data-ttu-id="baaec-111">Opis</span><span class="sxs-lookup"><span data-stu-id="baaec-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="baaec-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="baaec-112">S_OK</span></span>|<span data-ttu-id="baaec-113">Stan nadrzędny został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="baaec-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="baaec-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="baaec-114">E_FAIL</span></span>|<span data-ttu-id="baaec-115">Nie można zwrócić stanu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="baaec-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="baaec-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="baaec-116">E_INVALIDARG</span></span>|<span data-ttu-id="baaec-117">`pPotentialParentFrame`lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="baaec-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="baaec-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="baaec-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baaec-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="baaec-119">Remarks</span></span>  
 <span data-ttu-id="baaec-120">`IsMatchingParentFrame`zwraca `true` czy obiekt Frame przekazywany do metody jest elementem nadrzędnym obiektu Frame, dla którego Metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="baaec-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="baaec-121">Jeśli wywołasz metodę w ramce, która nie jest elementem podrzędnym określonej ramki, zwróci błąd.</span><span class="sxs-lookup"><span data-stu-id="baaec-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baaec-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="baaec-122">Requirements</span></span>  
 <span data-ttu-id="baaec-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baaec-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baaec-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="baaec-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="baaec-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="baaec-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baaec-126">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baaec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baaec-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="baaec-127">See also</span></span>

- [<span data-ttu-id="baaec-128">ICorDebugNativeFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="baaec-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="baaec-129">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="baaec-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="baaec-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="baaec-130">Debugging</span></span>](index.md)
