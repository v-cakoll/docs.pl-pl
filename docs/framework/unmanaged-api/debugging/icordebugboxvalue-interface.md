---
title: ICorDebugBoxValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue
helpviewer_keywords:
- ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3d3ae7e2-97d4-46de-a2c3-cb78f3490f9d
topic_type:
- apiref
ms.openlocfilehash: a40e12655106cca01add065c2f95384b0eb1a286
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122809"
---
# <a name="icordebugboxvalue-interface"></a><span data-ttu-id="930f4-102">ICorDebugBoxValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="930f4-102">ICorDebugBoxValue Interface</span></span>

<span data-ttu-id="930f4-103">Podklasa elementu "ICorDebugHeapValue" reprezentująca obiekt klasy wartości w ramce.</span><span class="sxs-lookup"><span data-stu-id="930f4-103">A subclass of "ICorDebugHeapValue" that represents a boxed value class object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="930f4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="930f4-104">Methods</span></span>  
  
|<span data-ttu-id="930f4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="930f4-105">Method</span></span>|<span data-ttu-id="930f4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="930f4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="930f4-107">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="930f4-107">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-getobject-method.md)|<span data-ttu-id="930f4-108">Pobiera wskaźnik interfejsu do zapakowanego wystąpienia "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="930f4-108">Gets an interface pointer to the boxed "ICorDebugObjectValue" instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="930f4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="930f4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="930f4-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="930f4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="930f4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="930f4-111">Requirements</span></span>  
 <span data-ttu-id="930f4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="930f4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="930f4-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="930f4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="930f4-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="930f4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="930f4-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="930f4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="930f4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="930f4-116">See also</span></span>

- [<span data-ttu-id="930f4-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="930f4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
