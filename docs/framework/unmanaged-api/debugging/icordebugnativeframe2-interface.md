---
title: "ICorDebugNativeFrame2 — Interfejs"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f501d49f007e22c6f7db0e759ee19b40f87b4b33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="734e4-102">ICorDebugNativeFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="734e4-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="734e4-103">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="734e4-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="734e4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="734e4-104">Methods</span></span>  
  
|<span data-ttu-id="734e4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="734e4-105">Method</span></span>|<span data-ttu-id="734e4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="734e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="734e4-107">IsChild, metoda</span><span class="sxs-lookup"><span data-stu-id="734e4-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="734e4-108">Określa, czy bieżącej ramki jest ramką podrzędną.</span><span class="sxs-lookup"><span data-stu-id="734e4-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="734e4-109">IsMatchingParentFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="734e4-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="734e4-110">Określa, czy określonej ramce nadrzędny bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="734e4-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="734e4-111">GetStackParameterSize, metoda</span><span class="sxs-lookup"><span data-stu-id="734e4-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="734e4-112">Zwraca całkowity rozmiar wszystkich parametrów na stosie na x86 systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="734e4-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="734e4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="734e4-113">Remarks</span></span>  
 <span data-ttu-id="734e4-114">Ten interfejs logicznie rozszerza interfejs "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="734e4-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="734e4-115">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="734e4-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="734e4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="734e4-116">Requirements</span></span>  
 <span data-ttu-id="734e4-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="734e4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="734e4-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="734e4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="734e4-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="734e4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="734e4-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="734e4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734e4-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="734e4-121">See Also</span></span>  
    
 [<span data-ttu-id="734e4-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="734e4-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="734e4-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="734e4-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
