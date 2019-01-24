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
ms.openlocfilehash: cc664d308d4db3e97597d785eda159e32255fa54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520376"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="b1c52-102">ICorDebugNativeFrame2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1c52-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="b1c52-103">Dostarcza metody testowania relacji podrzędnych i nadrzędnych ramek.</span><span class="sxs-lookup"><span data-stu-id="b1c52-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1c52-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b1c52-104">Methods</span></span>  
  
|<span data-ttu-id="b1c52-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1c52-105">Method</span></span>|<span data-ttu-id="b1c52-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b1c52-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1c52-107">IsChild, metoda</span><span class="sxs-lookup"><span data-stu-id="b1c52-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="b1c52-108">Określa, czy bieżące ramce ramki podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="b1c52-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="b1c52-109">IsMatchingParentFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="b1c52-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="b1c52-110">Określa, czy ramki o określonym nadrzędny bieżącej ramki.</span><span class="sxs-lookup"><span data-stu-id="b1c52-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="b1c52-111">GetStackParameterSize, metoda</span><span class="sxs-lookup"><span data-stu-id="b1c52-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="b1c52-112">Zwraca całkowity rozmiar wszystkich parametrów na stosie na x86 systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="b1c52-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1c52-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1c52-113">Remarks</span></span>  
 <span data-ttu-id="b1c52-114">Ten interfejs rozszerza logicznie interfejsu "icordebugnativeframe —".</span><span class="sxs-lookup"><span data-stu-id="b1c52-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1c52-115">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="b1c52-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c52-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1c52-116">Requirements</span></span>  
 <span data-ttu-id="b1c52-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c52-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c52-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1c52-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1c52-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1c52-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c52-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c52-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c52-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1c52-121">See also</span></span>

- [<span data-ttu-id="b1c52-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b1c52-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b1c52-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b1c52-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
