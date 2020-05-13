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
ms.openlocfilehash: 7c5359ddf2c021f77ad1ea0a8579316c3c773fd5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209789"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="85b80-102">ICorDebugGenericValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="85b80-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="85b80-103">Podklasa elementu "ICorDebugValue", która odnosi się do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="85b80-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="85b80-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="85b80-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85b80-105">Metody</span><span class="sxs-lookup"><span data-stu-id="85b80-105">Methods</span></span>  
  
|<span data-ttu-id="85b80-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="85b80-106">Method</span></span>|<span data-ttu-id="85b80-107">Opis</span><span class="sxs-lookup"><span data-stu-id="85b80-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85b80-108">GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="85b80-108">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="85b80-109">Kopiuje wartość do określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="85b80-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="85b80-110">SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="85b80-110">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="85b80-111">Kopiuje nową wartość z określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="85b80-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85b80-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85b80-112">Remarks</span></span>  
 <span data-ttu-id="85b80-113">`ICorDebugGenericValue`jest interfejsem podrzędnym, ponieważ nie jest zdalnie.</span><span class="sxs-lookup"><span data-stu-id="85b80-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="85b80-114">W przypadku typów referencyjnych wartością jest odwołanie, a nie zawartość odwołania.</span><span class="sxs-lookup"><span data-stu-id="85b80-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="85b80-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="85b80-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85b80-116">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="85b80-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b80-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85b80-117">Requirements</span></span>  
 <span data-ttu-id="85b80-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85b80-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85b80-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="85b80-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85b80-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="85b80-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85b80-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85b80-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b80-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85b80-122">See also</span></span>

- [<span data-ttu-id="85b80-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="85b80-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
