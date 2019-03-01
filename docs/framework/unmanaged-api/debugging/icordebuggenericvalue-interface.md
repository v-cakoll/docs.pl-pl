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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad2209c6e28c7749bd149902e5b696955ee7f13f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981988"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="02b1d-102">ICorDebugGenericValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="02b1d-102">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="02b1d-103">Podklasa klasy "ICorDebugValue", która ma zastosowanie do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="02b1d-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="02b1d-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="02b1d-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02b1d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="02b1d-105">Methods</span></span>  
  
|<span data-ttu-id="02b1d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="02b1d-106">Method</span></span>|<span data-ttu-id="02b1d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="02b1d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02b1d-108">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="02b1d-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="02b1d-109">Kopiuje wartość do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="02b1d-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="02b1d-110">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="02b1d-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="02b1d-111">Kopiuje nowej wartości z określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="02b1d-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02b1d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02b1d-112">Remarks</span></span>  
 <span data-ttu-id="02b1d-113">`ICorDebugGenericValue` jest interfejsem podrzędnych, ponieważ jest bez — może być zastosowana zdalnie.</span><span class="sxs-lookup"><span data-stu-id="02b1d-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="02b1d-114">Dla typów odwołań wartość jest odwołanie, a nie treści odwołania.</span><span class="sxs-lookup"><span data-stu-id="02b1d-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="02b1d-115">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="02b1d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02b1d-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="02b1d-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02b1d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02b1d-117">Requirements</span></span>  
 <span data-ttu-id="02b1d-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02b1d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02b1d-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02b1d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02b1d-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02b1d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02b1d-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02b1d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b1d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02b1d-122">See also</span></span>

- [<span data-ttu-id="02b1d-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="02b1d-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
