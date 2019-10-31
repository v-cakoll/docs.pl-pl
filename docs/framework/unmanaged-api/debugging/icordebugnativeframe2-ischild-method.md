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
ms.openlocfilehash: 539fa612234c4cc37bed5a8fd4b1e727a35b1d6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096392"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="ae481-102">ICorDebugNativeFrame2::IsChild — Metoda</span><span class="sxs-lookup"><span data-stu-id="ae481-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="ae481-103">Określa, czy bieżąca ramka jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="ae481-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae481-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae481-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae481-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ae481-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="ae481-106">określoną Wartość logiczna określająca, czy bieżąca ramka jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="ae481-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae481-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ae481-107">Return Value</span></span>  
 <span data-ttu-id="ae481-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="ae481-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ae481-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae481-109">HRESULT</span></span>|<span data-ttu-id="ae481-110">Opis</span><span class="sxs-lookup"><span data-stu-id="ae481-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae481-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae481-111">S_OK</span></span>|<span data-ttu-id="ae481-112">Pomyślnie zwrócono stan podrzędny.</span><span class="sxs-lookup"><span data-stu-id="ae481-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="ae481-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae481-113">E_FAIL</span></span>|<span data-ttu-id="ae481-114">Nie można zwrócić stanu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="ae481-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="ae481-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ae481-115">E_INVALIDARG</span></span>|<span data-ttu-id="ae481-116">`pIsChild` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="ae481-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ae481-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="ae481-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae481-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae481-118">Remarks</span></span>  
 <span data-ttu-id="ae481-119">Metoda `IsChild` zwraca `true`, jeśli obiekt ramki, dla którego wywoływana jest metoda, jest elementem podrzędnym innej ramki.</span><span class="sxs-lookup"><span data-stu-id="ae481-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="ae481-120">W takim przypadku należy użyć metody [IsMatchingParentFrame —](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) , aby sprawdzić, czy ramka jest nadrzędna.</span><span class="sxs-lookup"><span data-stu-id="ae481-120">If this is the case, use the [IsMatchingParentFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae481-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae481-121">Requirements</span></span>  
 <span data-ttu-id="ae481-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae481-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae481-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ae481-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae481-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ae481-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae481-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae481-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae481-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae481-126">See also</span></span>

- [<span data-ttu-id="ae481-127">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ae481-127">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)
- [<span data-ttu-id="ae481-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ae481-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ae481-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ae481-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
