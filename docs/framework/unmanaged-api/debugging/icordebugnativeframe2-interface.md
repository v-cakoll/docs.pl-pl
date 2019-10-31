---
title: ICorDebugNativeFrame2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: bff6dea0e870cf62734fa583eefa481c594481b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096521"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="6e459-102">ICorDebugNativeFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6e459-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="6e459-103">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="6e459-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e459-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6e459-104">Methods</span></span>  
  
|<span data-ttu-id="6e459-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e459-105">Method</span></span>|<span data-ttu-id="6e459-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6e459-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e459-107">IsChild, metoda</span><span class="sxs-lookup"><span data-stu-id="6e459-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="6e459-108">Określa, czy bieżąca ramka jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="6e459-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="6e459-109">IsMatchingParentFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="6e459-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="6e459-110">Określa, czy określona ramka jest elementem nadrzędnym bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="6e459-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="6e459-111">GetStackParameterSize, metoda</span><span class="sxs-lookup"><span data-stu-id="6e459-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="6e459-112">Zwraca skumulowany rozmiar parametrów na stosie w systemach operacyjnych x86.</span><span class="sxs-lookup"><span data-stu-id="6e459-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e459-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e459-113">Remarks</span></span>  
 <span data-ttu-id="6e459-114">Ten interfejs logicznie rozszerza interfejs "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="6e459-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e459-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6e459-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e459-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e459-116">Requirements</span></span>  
 <span data-ttu-id="6e459-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e459-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e459-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e459-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e459-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6e459-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e459-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e459-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e459-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6e459-121">See also</span></span>

- [<span data-ttu-id="6e459-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6e459-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6e459-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6e459-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
