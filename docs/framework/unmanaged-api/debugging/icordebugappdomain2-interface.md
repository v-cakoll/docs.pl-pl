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
ms.openlocfilehash: 5c6ef901f43cd6568f17657ed8e58bc2cc2cc0a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186059"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="0d35f-102">ICorDebugAppDomain2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0d35f-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="0d35f-103">Udostępnia metody do pracy z tablicami, wskaźników, wskaźników funkcji i typy odwołań.</span><span class="sxs-lookup"><span data-stu-id="0d35f-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="0d35f-104">Ten interfejs jest rozszerzeniem icordebugappdomain — interfejs.</span><span class="sxs-lookup"><span data-stu-id="0d35f-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d35f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0d35f-105">Methods</span></span>  
  
|<span data-ttu-id="0d35f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0d35f-106">Method</span></span>|<span data-ttu-id="0d35f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0d35f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d35f-108">GetArrayOrPointerType, metoda</span><span class="sxs-lookup"><span data-stu-id="0d35f-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="0d35f-109">Pobiera tablicę elementów określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="0d35f-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="0d35f-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="0d35f-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="0d35f-111">Pobiera wskaźnik do funkcji, która ma podpis danego.</span><span class="sxs-lookup"><span data-stu-id="0d35f-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d35f-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d35f-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d35f-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="0d35f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d35f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d35f-114">Requirements</span></span>  
 <span data-ttu-id="0d35f-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d35f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d35f-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0d35f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0d35f-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d35f-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0d35f-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0d35f-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d35f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d35f-119">See also</span></span>

- [<span data-ttu-id="0d35f-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="0d35f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
