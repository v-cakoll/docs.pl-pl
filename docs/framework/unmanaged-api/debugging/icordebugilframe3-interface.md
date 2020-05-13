---
title: ICorDebugILFrame3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: 59221b09cc1c5d2d01c1007b649a4bb01de57f04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213767"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="05532-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="05532-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="05532-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="05532-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="05532-104">`ICorDebugILFrame3`jest logicznym rozszerzeniem interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="05532-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05532-105">Metody</span><span class="sxs-lookup"><span data-stu-id="05532-105">Methods</span></span>  
  
|<span data-ttu-id="05532-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="05532-106">Method</span></span>|<span data-ttu-id="05532-107">Opis</span><span class="sxs-lookup"><span data-stu-id="05532-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05532-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="05532-108">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="05532-109">Pobiera obiekt ICorDebugValue, który hermetyzuje zwracaną wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="05532-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05532-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05532-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05532-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="05532-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05532-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05532-112">Requirements</span></span>  
 <span data-ttu-id="05532-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05532-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05532-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="05532-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05532-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="05532-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05532-116">**.NET Framework wersje:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05532-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05532-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05532-117">See also</span></span>

- [<span data-ttu-id="05532-118">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="05532-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="05532-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="05532-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
