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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912791"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="4a686-102">ICorDebugNativeFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4a686-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="4a686-103">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="4a686-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a686-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4a686-104">Methods</span></span>  
  
|<span data-ttu-id="4a686-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4a686-105">Method</span></span>|<span data-ttu-id="4a686-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4a686-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a686-107">IsChild, metoda</span><span class="sxs-lookup"><span data-stu-id="4a686-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="4a686-108">Określa, czy bieżąca ramka jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="4a686-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="4a686-109">IsMatchingParentFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="4a686-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="4a686-110">Określa, czy określona ramka jest elementem nadrzędnym bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="4a686-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="4a686-111">GetStackParameterSize, metoda</span><span class="sxs-lookup"><span data-stu-id="4a686-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="4a686-112">Zwraca skumulowany rozmiar parametrów na stosie w systemach operacyjnych x86.</span><span class="sxs-lookup"><span data-stu-id="4a686-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a686-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a686-113">Remarks</span></span>  
 <span data-ttu-id="4a686-114">Ten interfejs logicznie rozszerza interfejs "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="4a686-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a686-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="4a686-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a686-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a686-116">Requirements</span></span>  
 <span data-ttu-id="4a686-117">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a686-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a686-118">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a686-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a686-119">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a686-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a686-120">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a686-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a686-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a686-121">See also</span></span>

- [<span data-ttu-id="4a686-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4a686-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4a686-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4a686-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
