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
ms.openlocfilehash: 0a553f2cbac6110e82803e6d0dd872cfaa15d773
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099927"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="d96df-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="d96df-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="d96df-103">Określa, czy ramki o określonym nadrzędny bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="d96df-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d96df-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d96df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d96df-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="d96df-106">[in] Wskaźnik do obiektu ramki, który chcesz ocenić, czy stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="d96df-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="d96df-107">[out] `true` Jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d96df-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d96df-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d96df-108">Return Value</span></span>  
 <span data-ttu-id="d96df-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d96df-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d96df-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d96df-110">HRESULT</span></span>|<span data-ttu-id="d96df-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d96df-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d96df-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d96df-112">S_OK</span></span>|<span data-ttu-id="d96df-113">Stan nadrzędnej została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="d96df-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="d96df-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d96df-114">E_FAIL</span></span>|<span data-ttu-id="d96df-115">Nie można zwrócić stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="d96df-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="d96df-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d96df-116">E_INVALIDARG</span></span>|<span data-ttu-id="d96df-117">`pPotentialParentFrame` lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d96df-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d96df-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d96df-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d96df-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d96df-119">Remarks</span></span>  
 <span data-ttu-id="d96df-120">`IsMatchingParentFrame` Zwraca `true` Jeśli obiekt w ramce przekazać do metody jest elementem nadrzędnym wywołaniu metody obiekt w ramce.</span><span class="sxs-lookup"><span data-stu-id="d96df-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="d96df-121">Jeśli wywołasz metodę dla ramki, który nie jest elementem podrzędnym ramki o określonym zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="d96df-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96df-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d96df-122">Requirements</span></span>  
 <span data-ttu-id="d96df-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d96df-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d96df-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d96df-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d96df-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d96df-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d96df-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d96df-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96df-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d96df-127">See also</span></span>

- [<span data-ttu-id="d96df-128">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d96df-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="d96df-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d96df-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d96df-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d96df-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
