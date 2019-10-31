---
title: ICorDebugGenericValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 312b8b005998da44feb5ae24ab4a0a17bb948a3f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138572"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="b65b5-102">ICorDebugGenericValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b65b5-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="b65b5-103">Podklasa elementu "ICorDebugValue", która odnosi się do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="b65b5-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="b65b5-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="b65b5-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b65b5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b65b5-105">Methods</span></span>  
  
|<span data-ttu-id="b65b5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b65b5-106">Method</span></span>|<span data-ttu-id="b65b5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b65b5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b65b5-108">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b65b5-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="b65b5-109">Kopiuje wartość do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="b65b5-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="b65b5-110">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="b65b5-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="b65b5-111">Kopiuje nową wartość z określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="b65b5-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b65b5-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b65b5-112">Remarks</span></span>  
 <span data-ttu-id="b65b5-113">`ICorDebugGenericValue` jest interfejsem podrzędnym, ponieważ nie jest zdalnie.</span><span class="sxs-lookup"><span data-stu-id="b65b5-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="b65b5-114">W przypadku typów referencyjnych wartością jest odwołanie, a nie zawartość odwołania.</span><span class="sxs-lookup"><span data-stu-id="b65b5-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="b65b5-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b65b5-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b65b5-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b65b5-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b65b5-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b65b5-117">Requirements</span></span>  
 <span data-ttu-id="b65b5-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b65b5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b65b5-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b65b5-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b65b5-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b65b5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b65b5-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b65b5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65b5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b65b5-122">See also</span></span>

- [<span data-ttu-id="b65b5-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b65b5-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
