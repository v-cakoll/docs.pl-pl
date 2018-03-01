---
title: ICorDebugAppDomain2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c811107fcf32696aee17810af06ac0b2ddc9102d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="8145a-102">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="8145a-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="8145a-103">Udostępnia metody do pracy z tablic, wskaźników, wskaźników funkcji i typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="8145a-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="8145a-104">Ten interfejs jest rozszerzenie interfejsu ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="8145a-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8145a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8145a-105">Methods</span></span>  
  
|<span data-ttu-id="8145a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8145a-106">Method</span></span>|<span data-ttu-id="8145a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8145a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8145a-108">GetArrayOrPointerType, metoda</span><span class="sxs-lookup"><span data-stu-id="8145a-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="8145a-109">Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="8145a-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="8145a-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="8145a-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="8145a-111">Pobiera wskaźnik do funkcji, która ma danym podpisem.</span><span class="sxs-lookup"><span data-stu-id="8145a-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8145a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8145a-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8145a-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="8145a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8145a-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8145a-114">Requirements</span></span>  
 <span data-ttu-id="8145a-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8145a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8145a-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8145a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8145a-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8145a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8145a-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8145a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8145a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8145a-119">See Also</span></span>  
 [<span data-ttu-id="8145a-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8145a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
