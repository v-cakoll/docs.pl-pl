---
title: ICorDebugAppDomain2, interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63772c6642cc6f7f96a375beab4f7ef1b4884139
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959842"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="9ecce-102">ICorDebugAppDomain2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9ecce-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="9ecce-103">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="9ecce-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="9ecce-104">Ten interfejs jest rozszerzeniem interfejsu ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="9ecce-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ecce-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9ecce-105">Methods</span></span>  
  
|<span data-ttu-id="9ecce-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ecce-106">Method</span></span>|<span data-ttu-id="9ecce-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9ecce-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ecce-108">GetArrayOrPointerType, metoda</span><span class="sxs-lookup"><span data-stu-id="9ecce-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="9ecce-109">Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="9ecce-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="9ecce-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="9ecce-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="9ecce-111">Pobiera wskaźnik do funkcji, która ma daną sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="9ecce-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ecce-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ecce-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ecce-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="9ecce-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ecce-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ecce-114">Requirements</span></span>  
 <span data-ttu-id="9ecce-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ecce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ecce-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ecce-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ecce-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ecce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ecce-118">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ecce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ecce-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ecce-119">See also</span></span>

- [<span data-ttu-id="9ecce-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9ecce-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
