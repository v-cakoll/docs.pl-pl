---
title: ICorDebugGenericValue, interfejs
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
ms.openlocfilehash: e60d4b128bf03ff81863e0c95815b2c204807583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794470"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="96bda-102">ICorDebugGenericValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="96bda-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="96bda-103">Podklasa elementu "ICorDebugValue", która odnosi się do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="96bda-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="96bda-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="96bda-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="96bda-105">Metody</span><span class="sxs-lookup"><span data-stu-id="96bda-105">Methods</span></span>  
  
|<span data-ttu-id="96bda-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="96bda-106">Method</span></span>|<span data-ttu-id="96bda-107">Opis</span><span class="sxs-lookup"><span data-stu-id="96bda-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="96bda-108">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="96bda-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="96bda-109">Kopiuje wartość do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="96bda-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="96bda-110">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="96bda-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="96bda-111">Kopiuje nową wartość z określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="96bda-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96bda-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96bda-112">Remarks</span></span>  
 <span data-ttu-id="96bda-113">`ICorDebugGenericValue` jest interfejsem podrzędnym, ponieważ nie jest zdalnie.</span><span class="sxs-lookup"><span data-stu-id="96bda-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="96bda-114">W przypadku typów referencyjnych wartością jest odwołanie, a nie zawartość odwołania.</span><span class="sxs-lookup"><span data-stu-id="96bda-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="96bda-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="96bda-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96bda-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="96bda-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96bda-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96bda-117">Requirements</span></span>  
 <span data-ttu-id="96bda-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96bda-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96bda-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="96bda-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96bda-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="96bda-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96bda-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96bda-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96bda-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96bda-122">See also</span></span>

- [<span data-ttu-id="96bda-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="96bda-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
