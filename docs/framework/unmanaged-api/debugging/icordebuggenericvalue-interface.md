---
title: ICorDebugGenericValue, interfejs1
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
ms.openlocfilehash: ce4c1b73ab806958627bb68bfdcfcae890bc5e67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709835"
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="f0c81-102">ICorDebugGenericValue, interfejs1</span><span class="sxs-lookup"><span data-stu-id="f0c81-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="f0c81-103">Podklasa klasy "ICorDebugValue", która ma zastosowanie do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="f0c81-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="f0c81-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="f0c81-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0c81-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f0c81-105">Methods</span></span>  
  
|<span data-ttu-id="f0c81-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0c81-106">Method</span></span>|<span data-ttu-id="f0c81-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f0c81-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0c81-108">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f0c81-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="f0c81-109">Kopiuje wartość do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="f0c81-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="f0c81-110">SetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="f0c81-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="f0c81-111">Kopiuje nowej wartości z określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="f0c81-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0c81-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0c81-112">Remarks</span></span>  
 <span data-ttu-id="f0c81-113">`ICorDebugGenericValue` jest interfejsem podrzędnych, ponieważ jest bez — może być zastosowana zdalnie.</span><span class="sxs-lookup"><span data-stu-id="f0c81-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="f0c81-114">Dla typów odwołań wartość jest odwołanie, a nie treści odwołania.</span><span class="sxs-lookup"><span data-stu-id="f0c81-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="f0c81-115">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f0c81-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0c81-116">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f0c81-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0c81-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0c81-117">Requirements</span></span>  
 <span data-ttu-id="f0c81-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0c81-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0c81-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0c81-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0c81-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0c81-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0c81-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0c81-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c81-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0c81-122">See also</span></span>

- [<span data-ttu-id="f0c81-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0c81-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
