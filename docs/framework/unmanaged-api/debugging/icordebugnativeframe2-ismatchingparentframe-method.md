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
ms.openlocfilehash: aeaa706ef35413a728f8b254cd325f0bcc83acd1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792712"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="60dad-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="60dad-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="60dad-103">Określa, czy określona ramka jest elementem nadrzędnym bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="60dad-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60dad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="60dad-104">Syntax</span></span>  
  
```cpp  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60dad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60dad-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="60dad-106">podczas Wskaźnik do obiektu Frame, który chcesz oszacować dla stanu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60dad-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="60dad-107">[out] `true`, jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="60dad-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60dad-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="60dad-108">Return Value</span></span>  
 <span data-ttu-id="60dad-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="60dad-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="60dad-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60dad-110">HRESULT</span></span>|<span data-ttu-id="60dad-111">Opis</span><span class="sxs-lookup"><span data-stu-id="60dad-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="60dad-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="60dad-112">S_OK</span></span>|<span data-ttu-id="60dad-113">Stan nadrzędny został pomyślnie zwrócony.</span><span class="sxs-lookup"><span data-stu-id="60dad-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="60dad-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="60dad-114">E_FAIL</span></span>|<span data-ttu-id="60dad-115">Nie można zwrócić stanu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="60dad-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="60dad-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="60dad-116">E_INVALIDARG</span></span>|<span data-ttu-id="60dad-117">`pPotentialParentFrame` lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="60dad-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="60dad-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="60dad-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60dad-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="60dad-119">Remarks</span></span>  
 <span data-ttu-id="60dad-120">`IsMatchingParentFrame` zwraca `true`, jeśli obiekt ramki przekazywany do metody jest elementem nadrzędnym obiektu ramki, na którym metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="60dad-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="60dad-121">Jeśli wywołasz metodę w ramce, która nie jest elementem podrzędnym określonej ramki, zwróci błąd.</span><span class="sxs-lookup"><span data-stu-id="60dad-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60dad-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="60dad-122">Requirements</span></span>  
 <span data-ttu-id="60dad-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60dad-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60dad-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="60dad-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60dad-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="60dad-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60dad-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60dad-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60dad-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60dad-127">See also</span></span>

- [<span data-ttu-id="60dad-128">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="60dad-128">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="60dad-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="60dad-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="60dad-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="60dad-130">Debugging</span></span>](index.md)
