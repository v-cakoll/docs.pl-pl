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
ms.openlocfilehash: 739c648173d45a9c147ea2a4e469a3a4b518e893
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794332"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="9720c-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9720c-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="9720c-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="9720c-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="9720c-104">`ICorDebugILFrame3` jest logicznym rozszerzeniem interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="9720c-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9720c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9720c-105">Methods</span></span>  
  
|<span data-ttu-id="9720c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9720c-106">Method</span></span>|<span data-ttu-id="9720c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9720c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9720c-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="9720c-108">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="9720c-109">Pobiera obiekt ICorDebugValue, który hermetyzuje zwracaną wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="9720c-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9720c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9720c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9720c-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="9720c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9720c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9720c-112">Requirements</span></span>  
 <span data-ttu-id="9720c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9720c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9720c-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9720c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9720c-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9720c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9720c-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9720c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9720c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9720c-117">See also</span></span>

- [<span data-ttu-id="9720c-118">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="9720c-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="9720c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9720c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
