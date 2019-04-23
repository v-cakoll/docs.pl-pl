---
title: ICorDebugNativeFrame2::IsChild — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9503c12da9e98fbd43f3904aad25c5d10655cec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075564"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="f6646-102">ICorDebugNativeFrame2::IsChild — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6646-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="f6646-103">Określa, czy bieżące ramce ramki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6646-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6646-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6646-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6646-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6646-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="f6646-106">[out] Wartość logiczna określająca, czy bieżące ramce jest ramki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="f6646-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6646-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f6646-107">Return Value</span></span>  
 <span data-ttu-id="f6646-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="f6646-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f6646-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f6646-109">HRESULT</span></span>|<span data-ttu-id="f6646-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f6646-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f6646-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f6646-111">S_OK</span></span>|<span data-ttu-id="f6646-112">Stan podrzędnego została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="f6646-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="f6646-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f6646-113">E_FAIL</span></span>|<span data-ttu-id="f6646-114">Stan podrzędnego nie mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="f6646-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="f6646-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f6646-115">E_INVALIDARG</span></span>|<span data-ttu-id="f6646-116">`pIsChild` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f6646-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="f6646-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="f6646-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6646-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6646-118">Remarks</span></span>  
 <span data-ttu-id="f6646-119">`IsChild` Metoda zwraca `true` Jeśli obiekt ramki, na którym należy wywołać metodę jest elementem podrzędnym innej ramki.</span><span class="sxs-lookup"><span data-stu-id="f6646-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="f6646-120">Jeśli jest to możliwe, należy użyć [ismatchingparentframe —](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metodę sprawdzania, czy dana ramka jest jego obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f6646-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6646-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6646-121">Requirements</span></span>  
 <span data-ttu-id="f6646-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6646-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6646-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6646-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6646-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6646-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6646-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6646-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6646-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6646-126">See also</span></span>

- [<span data-ttu-id="f6646-127">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6646-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="f6646-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f6646-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f6646-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f6646-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
