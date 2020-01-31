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
ms.openlocfilehash: 22722e4d602bdb9df9877b2199b4d4271a4d3105
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792731"
---
# <a name="icordebugnativeframe2ischild-method"></a><span data-ttu-id="d6153-102">ICorDebugNativeFrame2::IsChild — Metoda</span><span class="sxs-lookup"><span data-stu-id="d6153-102">ICorDebugNativeFrame2::IsChild Method</span></span>
<span data-ttu-id="d6153-103">Określa, czy bieżąca ramka jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="d6153-103">Determines whether the current frame is a child frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6153-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6153-104">Syntax</span></span>  
  
```cpp  
HRESULT IsChild([out] BOOL * pIsChild);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6153-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6153-105">Parameters</span></span>  
 `pIsChild`  
 <span data-ttu-id="d6153-106">określoną Wartość logiczna określająca, czy bieżąca ramka jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="d6153-106">[out] A Boolean value that specifies whether the current frame is a child frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6153-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d6153-107">Return Value</span></span>  
 <span data-ttu-id="d6153-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d6153-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d6153-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6153-109">HRESULT</span></span>|<span data-ttu-id="d6153-110">Opis</span><span class="sxs-lookup"><span data-stu-id="d6153-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6153-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6153-111">S_OK</span></span>|<span data-ttu-id="d6153-112">Pomyślnie zwrócono stan podrzędny.</span><span class="sxs-lookup"><span data-stu-id="d6153-112">The child status was successfully returned.</span></span>|  
|<span data-ttu-id="d6153-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6153-113">E_FAIL</span></span>|<span data-ttu-id="d6153-114">Nie można zwrócić stanu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d6153-114">The child status could not be returned.</span></span>|  
|<span data-ttu-id="d6153-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d6153-115">E_INVALIDARG</span></span>|<span data-ttu-id="d6153-116">Parametr `pIsChild` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d6153-116">`pIsChild` is null.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="d6153-117">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d6153-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6153-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6153-118">Remarks</span></span>  
 <span data-ttu-id="d6153-119">Metoda `IsChild` zwraca `true`, jeśli obiekt ramki, dla którego wywoływana jest metoda, jest elementem podrzędnym innej ramki.</span><span class="sxs-lookup"><span data-stu-id="d6153-119">The `IsChild` method returns `true` if the frame object on which you call the method is a child of another frame.</span></span> <span data-ttu-id="d6153-120">W takim przypadku należy użyć metody [IsMatchingParentFrame —](icordebugnativeframe2-ismatchingparentframe-method.md) , aby sprawdzić, czy ramka jest nadrzędna.</span><span class="sxs-lookup"><span data-stu-id="d6153-120">If this is the case, use the [IsMatchingParentFrame](icordebugnativeframe2-ismatchingparentframe-method.md) method to check whether a frame is its parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6153-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6153-121">Requirements</span></span>  
 <span data-ttu-id="d6153-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6153-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6153-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d6153-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6153-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d6153-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6153-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6153-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6153-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6153-126">See also</span></span>

- [<span data-ttu-id="d6153-127">ICorDebugNativeFrame2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d6153-127">ICorDebugNativeFrame2 Interface</span></span>](icordebugnativeframe2-interface.md)
- [<span data-ttu-id="d6153-128">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d6153-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d6153-129">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d6153-129">Debugging</span></span>](index.md)
