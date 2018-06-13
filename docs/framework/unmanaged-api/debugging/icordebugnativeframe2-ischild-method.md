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
ms.openlocfilehash: d9d613e810724b8e133b490c17a37ecc6565f09a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419390"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="4d405-102">ICorDebugNativeFrame2::IsChild — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d405-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="4d405-103">Określa, czy bieżącej ramki jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="4d405-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d405-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d405-104">Syntax</span></span>  
  
```  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d405-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d405-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="4d405-106">[out] Wartość logiczna określająca, czy bieżącej ramki jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="4d405-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d405-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4d405-107">Return Value</span></span>  
 <span data-ttu-id="4d405-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="4d405-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4d405-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d405-109">HRESULT</span></span>|<span data-ttu-id="4d405-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4d405-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d405-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d405-111">S_OK</span></span>|<span data-ttu-id="4d405-112">Pomyślnie zwrócono stanu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4d405-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="4d405-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4d405-113">E_FAIL</span></span>|<span data-ttu-id="4d405-114">Nie można zwrócić stanu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4d405-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="4d405-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4d405-115">E_INVALIDARG</span></span>|<span data-ttu-id="4d405-116">`pIsChild` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="4d405-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="4d405-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="4d405-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d405-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d405-118">Remarks</span></span>  
 <span data-ttu-id="4d405-119">`IsChild` Metoda zwraca `true` Jeśli obiekt ramki, na którym należy wywołać metodę jest elementem podrzędnym innej ramki.</span><span class="sxs-lookup"><span data-stu-id="4d405-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="4d405-120">Jeśli jest to możliwe, użyj [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) , aby sprawdzić, czy dana ramka jest jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="4d405-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d405-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d405-121">Requirements</span></span>  
 <span data-ttu-id="4d405-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d405-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d405-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d405-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d405-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d405-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d405-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d405-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d405-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d405-126">See Also</span></span>  
 [<span data-ttu-id="4d405-127">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d405-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [<span data-ttu-id="4d405-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4d405-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4d405-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4d405-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
