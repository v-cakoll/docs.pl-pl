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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075564"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="bf841-102">ICorDebugNativeFrame2::IsChild — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf841-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="bf841-103">Określa, czy bieżące ramce ramki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="bf841-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf841-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf841-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf841-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf841-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="bf841-106">[out] Wartość logiczna określająca, czy bieżące ramce jest ramki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="bf841-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf841-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bf841-107">Return Value</span></span>  
 <span data-ttu-id="bf841-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="bf841-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bf841-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf841-109">HRESULT</span></span>|<span data-ttu-id="bf841-110">Opis</span><span class="sxs-lookup"><span data-stu-id="bf841-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf841-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf841-111">S_OK</span></span>|<span data-ttu-id="bf841-112">Stan podrzędnego została pomyślnie zwrócona.</span><span class="sxs-lookup"><span data-stu-id="bf841-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="bf841-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bf841-113">E_FAIL</span></span>|<span data-ttu-id="bf841-114">Stan podrzędnego nie mogą być zwracane.</span><span class="sxs-lookup"><span data-stu-id="bf841-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="bf841-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bf841-115">E_INVALIDARG</span></span>|`pIsChild` <span data-ttu-id="bf841-116">ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="bf841-116">is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="bf841-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="bf841-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf841-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf841-118">Remarks</span></span>  
 <span data-ttu-id="bf841-119">`IsChild` Metoda zwraca `true` Jeśli obiekt ramki, na którym należy wywołać metodę jest elementem podrzędnym innej ramki.</span><span class="sxs-lookup"><span data-stu-id="bf841-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="bf841-120">Jeśli jest to możliwe, należy użyć [ismatchingparentframe —](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) metodę sprawdzania, czy dana ramka jest jego obiektu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="bf841-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf841-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf841-121">Requirements</span></span>  
 <span data-ttu-id="bf841-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf841-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf841-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf841-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf841-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf841-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="bf841-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bf841-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf841-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf841-126">See also</span></span>

- [<span data-ttu-id="bf841-127">ICorDebugNativeFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bf841-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="bf841-128">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="bf841-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bf841-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bf841-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
