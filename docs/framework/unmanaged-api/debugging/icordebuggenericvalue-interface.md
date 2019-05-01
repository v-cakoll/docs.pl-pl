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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988679"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="5b0ea-102">ICorDebugGenericValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="5b0ea-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="5b0ea-103">Podklasa klasy "ICorDebugValue", która ma zastosowanie do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="5b0ea-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b0ea-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5b0ea-105">Methods</span></span>  
  
|<span data-ttu-id="5b0ea-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b0ea-106">Method</span></span>|<span data-ttu-id="5b0ea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5b0ea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b0ea-108">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="5b0ea-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="5b0ea-109">Kopiuje wartość do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="5b0ea-110">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="5b0ea-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="5b0ea-111">Kopiuje nowej wartości z określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b0ea-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b0ea-112">Remarks</span></span>  
 <span data-ttu-id="5b0ea-113">`ICorDebugGenericValue` jest interfejsem podrzędnych, ponieważ jest bez — może być zastosowana zdalnie.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="5b0ea-114">Dla typów odwołań wartość jest odwołanie, a nie treści odwołania.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="5b0ea-115">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b0ea-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5b0ea-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b0ea-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5b0ea-117">Requirements</span></span>  
 <span data-ttu-id="5b0ea-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b0ea-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b0ea-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b0ea-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b0ea-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b0ea-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b0ea-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b0ea-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0ea-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b0ea-122">See also</span></span>

- [<span data-ttu-id="5b0ea-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5b0ea-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
