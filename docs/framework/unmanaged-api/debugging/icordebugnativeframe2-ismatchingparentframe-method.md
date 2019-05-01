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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987834"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="178c0-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="178c0-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="178c0-103">Określa, czy ramki o określonym nadrzędny bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="178c0-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="178c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="178c0-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
## <a name="parameters"></a><span data-ttu-id="178c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="178c0-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="178c0-106">[in] Wskaźnik do obiektu ramki, który chcesz ocenić, czy stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="178c0-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="178c0-107">[out] `true` Jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="178c0-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="178c0-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="178c0-108">Return Value</span></span>  
 <span data-ttu-id="178c0-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="178c0-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="178c0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="178c0-110">HRESULT</span></span>|<span data-ttu-id="178c0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="178c0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="178c0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="178c0-112">S_OK</span></span>|<span data-ttu-id="178c0-113">Stan nadrzędnej została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="178c0-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="178c0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="178c0-114">E_FAIL</span></span>|<span data-ttu-id="178c0-115">Nie można zwrócić stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="178c0-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="178c0-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="178c0-116">E_INVALIDARG</span></span>|<span data-ttu-id="178c0-117">`pPotentialParentFrame` lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="178c0-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="178c0-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="178c0-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="178c0-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="178c0-119">Remarks</span></span>  
 <span data-ttu-id="178c0-120">`IsMatchingParentFrame` Zwraca `true` Jeśli obiekt w ramce przekazać do metody jest elementem nadrzędnym wywołaniu metody obiekt w ramce.</span><span class="sxs-lookup"><span data-stu-id="178c0-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="178c0-121">Jeśli wywołasz metodę dla ramki, który nie jest elementem podrzędnym ramki o określonym zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="178c0-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="178c0-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="178c0-122">Requirements</span></span>  
 <span data-ttu-id="178c0-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="178c0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="178c0-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="178c0-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="178c0-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="178c0-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="178c0-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="178c0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="178c0-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="178c0-127">See also</span></span>

- [<span data-ttu-id="178c0-128">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="178c0-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="178c0-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="178c0-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="178c0-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="178c0-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
