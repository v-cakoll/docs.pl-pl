---
title: ICorDebugAppDomain2 Interface1
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
ms.openlocfilehash: f4549b0fe6379979a7b9bd6344d65ff465f33f17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506137"
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="81ccc-102">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="81ccc-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="81ccc-103">Udostępnia metody do pracy z tablicami, wskaźników, wskaźników funkcji i typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="81ccc-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="81ccc-104">Ten interfejs jest rozszerzeniem icordebugappdomain — interfejs.</span><span class="sxs-lookup"><span data-stu-id="81ccc-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81ccc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="81ccc-105">Methods</span></span>  
  
|<span data-ttu-id="81ccc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="81ccc-106">Method</span></span>|<span data-ttu-id="81ccc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="81ccc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81ccc-108">GetArrayOrPointerType, metoda</span><span class="sxs-lookup"><span data-stu-id="81ccc-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="81ccc-109">Pobiera tablicę elementów określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="81ccc-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="81ccc-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="81ccc-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="81ccc-111">Pobiera wskaźnik do funkcji, która ma podpis danego.</span><span class="sxs-lookup"><span data-stu-id="81ccc-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81ccc-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81ccc-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81ccc-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="81ccc-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ccc-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81ccc-114">Requirements</span></span>  
 <span data-ttu-id="81ccc-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81ccc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ccc-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81ccc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81ccc-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81ccc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81ccc-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ccc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ccc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81ccc-119">See also</span></span>
- [<span data-ttu-id="81ccc-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="81ccc-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
