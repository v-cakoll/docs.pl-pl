---
title: "ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fc2d8eacb05e861290ad19a34c261943dc2959a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a><span data-ttu-id="cf9a9-102">ICorDebugNativeFrame2::IsMatchingParentFrame — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf9a9-102">ICorDebugNativeFrame2::IsMatchingParentFrame Method</span></span>
<span data-ttu-id="cf9a9-103">Określa, czy określonej ramce nadrzędny bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-103">Determines whether the specified frame is the parent of the current frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf9a9-104">Syntax</span></span>  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf9a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf9a9-105">Parameters</span></span>  
 `pPotentialParentFrame`  
 <span data-ttu-id="cf9a9-106">[in] Wskaźnik do obiektu ramki, który chcesz ocenić stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-106">[in] A pointer to the frame object that you want to evaluate for parent status.</span></span>  
  
 `pIsParent`  
 <span data-ttu-id="cf9a9-107">[out] `true` Jeśli `pPotentialParentFrame` jest elementem nadrzędnym bieżącej ramki; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-107">[out] `true` if `pPotentialParentFrame` is the current frame’s parent; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf9a9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cf9a9-108">Return Value</span></span>  
 <span data-ttu-id="cf9a9-109">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cf9a9-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cf9a9-110">HRESULT</span></span>|<span data-ttu-id="cf9a9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="cf9a9-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cf9a9-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cf9a9-112">S_OK</span></span>|<span data-ttu-id="cf9a9-113">Pomyślnie zwrócono stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-113">The parent status was successfully returned.</span></span>|  
|<span data-ttu-id="cf9a9-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cf9a9-114">E_FAIL</span></span>|<span data-ttu-id="cf9a9-115">Nie można zwrócić stan nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-115">The parent status could not be returned.</span></span>|  
|<span data-ttu-id="cf9a9-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cf9a9-116">E_INVALIDARG</span></span>|<span data-ttu-id="cf9a9-117">`pPotentialParentFrame`lub `pIsParent` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-117">`pPotentialParentFrame` or `pIsParent` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="cf9a9-118">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cf9a9-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf9a9-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf9a9-119">Remarks</span></span>  
 <span data-ttu-id="cf9a9-120">`IsMatchingParentFrame`Zwraca `true` Jeśli obiekt ramki przekazać do metody jest elementem nadrzędnym obiektu ramki, wywołania tej metody.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-120">`IsMatchingParentFrame` returns `true` if the frame object you pass to the method is the parent of the frame object on which the method was called.</span></span> <span data-ttu-id="cf9a9-121">Jeśli należy wywołać metodę ramki, który nie jest elementem podrzędnym określonej ramce zwraca błąd.</span><span class="sxs-lookup"><span data-stu-id="cf9a9-121">If you call the method on a frame that is not a child of the specified frame, it returns an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf9a9-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cf9a9-122">Requirements</span></span>  
 <span data-ttu-id="cf9a9-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf9a9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9a9-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf9a9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf9a9-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf9a9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf9a9-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf9a9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9a9-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cf9a9-127">See Also</span></span>  
 [<span data-ttu-id="cf9a9-128">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cf9a9-128">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="cf9a9-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cf9a9-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="cf9a9-130">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="cf9a9-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
