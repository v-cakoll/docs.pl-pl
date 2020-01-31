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
ms.openlocfilehash: 6f9bcec66ff613d19c1198ac9849ca28c978f537
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788946"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="1a568-102">ICorDebugAppDomain2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a568-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="1a568-103">Dostarcza metody do pracy z tablicami, wskaźnikami, wskaźnikami funkcji i typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="1a568-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="1a568-104">Ten interfejs jest rozszerzeniem interfejsu ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="1a568-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a568-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1a568-105">Methods</span></span>  
  
|<span data-ttu-id="1a568-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1a568-106">Method</span></span>|<span data-ttu-id="1a568-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1a568-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a568-108">GetArrayOrPointerType, metoda</span><span class="sxs-lookup"><span data-stu-id="1a568-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="1a568-109">Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="1a568-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="1a568-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="1a568-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="1a568-111">Pobiera wskaźnik do funkcji, która ma daną sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="1a568-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a568-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a568-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a568-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="1a568-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a568-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a568-114">Requirements</span></span>  
 <span data-ttu-id="1a568-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a568-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a568-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a568-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a568-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1a568-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a568-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a568-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a568-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a568-119">See also</span></span>

- [<span data-ttu-id="1a568-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1a568-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
