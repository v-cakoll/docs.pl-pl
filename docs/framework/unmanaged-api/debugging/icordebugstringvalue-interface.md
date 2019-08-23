---
title: ICorDebugStringValue, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cfaf886d09d843f4dbf61af55a9388454b050ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957424"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="5339c-102">ICorDebugStringValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="5339c-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="5339c-103">Podklasa elementu ICorDebugHeapValue, która ma zastosowanie do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="5339c-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5339c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5339c-104">Methods</span></span>  
  
|<span data-ttu-id="5339c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5339c-105">Method</span></span>|<span data-ttu-id="5339c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5339c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5339c-107">GetLength, metoda</span><span class="sxs-lookup"><span data-stu-id="5339c-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="5339c-108">Pobiera liczbę znaków w ciągu, do którego się odwołuje `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="5339c-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="5339c-109">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="5339c-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="5339c-110">Pobiera ciąg, do którego się `ICorDebugStringValue`odwołuje.</span><span class="sxs-lookup"><span data-stu-id="5339c-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5339c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5339c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5339c-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="5339c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5339c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5339c-113">Requirements</span></span>  
 <span data-ttu-id="5339c-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5339c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5339c-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5339c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5339c-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5339c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5339c-117">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5339c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5339c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5339c-118">See also</span></span>

- [<span data-ttu-id="5339c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5339c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
