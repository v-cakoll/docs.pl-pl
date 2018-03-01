---
title: "ICorDebugNativeFrame2::IsChild — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugNativeFrame2.IsChild Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsChild
helpviewer_keywords:
- IsChild method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsChild method [.NET Framework debugging]
ms.assetid: 9e2aae09-49cb-4fbd-81e5-e29cd864a88b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 267bc2fcd03786bfceb218dd0218ffa7006f8fa7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="f9e10-102">ICorDebugNativeFrame2::IsChild — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9e10-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="f9e10-103">Określa, czy bieżącej ramki jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="f9e10-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9e10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9e10-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9e10-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9e10-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="f9e10-106">[out] Wartość logiczna określająca, czy bieżącej ramki jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="f9e10-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9e10-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f9e10-107">Return Value</span></span>  
 <span data-ttu-id="f9e10-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="f9e10-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f9e10-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f9e10-109">HRESULT</span></span>|<span data-ttu-id="f9e10-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f9e10-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f9e10-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f9e10-111">S_OK</span></span>|<span data-ttu-id="f9e10-112">Pomyślnie zwrócono stanu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f9e10-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="f9e10-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f9e10-113">E_FAIL</span></span>|<span data-ttu-id="f9e10-114">Nie można zwrócić stanu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f9e10-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="f9e10-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f9e10-115">E_INVALIDARG</span></span>|<span data-ttu-id="f9e10-116">`pIsChild`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f9e10-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f9e10-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f9e10-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9e10-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9e10-118">Remarks</span></span>  
 <span data-ttu-id="f9e10-119">`IsChild` Metoda zwraca `true` Jeśli obiekt ramki, na którym należy wywołać metodę jest elementem podrzędnym innej ramki.</span><span class="sxs-lookup"><span data-stu-id="f9e10-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="f9e10-120">Jeśli jest to możliwe, użyj [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) , aby sprawdzić, czy dana ramka jest jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f9e10-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9e10-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9e10-121">Requirements</span></span>  
 <span data-ttu-id="f9e10-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9e10-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9e10-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9e10-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9e10-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9e10-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9e10-125">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9e10-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9e10-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9e10-126">See Also</span></span>  
 [<span data-ttu-id="f9e10-127">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f9e10-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="f9e10-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f9e10-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f9e10-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f9e10-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
