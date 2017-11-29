---
title: ICorDebugGenericValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGenericValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGenericValue
helpviewer_keywords: ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c159e30efb33dca4043e5b5306c9544acd614a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebuggenericvalue-interface1"></a><span data-ttu-id="a5e89-102">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="a5e89-102">ICorDebugGenericValue Interface1</span></span>
<span data-ttu-id="a5e89-103">Podklasa "ICorDebugValue", która ma zastosowanie do wszystkich wartości.</span><span class="sxs-lookup"><span data-stu-id="a5e89-103">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="a5e89-104">Ten interfejs zapewnia metody Get i Set dla wartości.</span><span class="sxs-lookup"><span data-stu-id="a5e89-104">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5e89-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a5e89-105">Methods</span></span>  
  
|<span data-ttu-id="a5e89-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a5e89-106">Method</span></span>|<span data-ttu-id="a5e89-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a5e89-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5e89-108">GetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="a5e89-108">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="a5e89-109">Skopiowanie wartości do określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="a5e89-109">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="a5e89-110">SetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="a5e89-110">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="a5e89-111">Kopiuje nową wartość z określonego bufora.</span><span class="sxs-lookup"><span data-stu-id="a5e89-111">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5e89-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5e89-112">Remarks</span></span>  
 <span data-ttu-id="a5e89-113">`ICorDebugGenericValue`jest interfejsem podrzędnych, ponieważ jest nie obsługują uruchamiania zdalnego.</span><span class="sxs-lookup"><span data-stu-id="a5e89-113">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="a5e89-114">Dla typów referencyjnych wartość jest odwołanie, a nie treści odwołania.</span><span class="sxs-lookup"><span data-stu-id="a5e89-114">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="a5e89-115">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="a5e89-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5e89-116">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="a5e89-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e89-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5e89-117">Requirements</span></span>  
 <span data-ttu-id="a5e89-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5e89-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e89-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5e89-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5e89-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e89-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e89-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e89-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e89-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5e89-122">See Also</span></span>  
    
 [<span data-ttu-id="a5e89-123">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="a5e89-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
