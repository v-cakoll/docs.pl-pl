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
ms.openlocfilehash: 6c232163f7c18086804eca7990a0890a507ef00b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791685"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="aee1f-102">ICorDebugStringValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="aee1f-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="aee1f-103">Podklasa elementu ICorDebugHeapValue, która ma zastosowanie do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="aee1f-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aee1f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="aee1f-104">Methods</span></span>  
  
|<span data-ttu-id="aee1f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="aee1f-105">Method</span></span>|<span data-ttu-id="aee1f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="aee1f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aee1f-107">GetLength, metoda</span><span class="sxs-lookup"><span data-stu-id="aee1f-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="aee1f-108">Pobiera liczbę znaków w ciągu, do których odwołuje się ten `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="aee1f-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="aee1f-109">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="aee1f-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="aee1f-110">Pobiera ciąg, do którego odwołuje się ten `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="aee1f-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aee1f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aee1f-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aee1f-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="aee1f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aee1f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aee1f-113">Requirements</span></span>  
 <span data-ttu-id="aee1f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aee1f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aee1f-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aee1f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aee1f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="aee1f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aee1f-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aee1f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee1f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aee1f-118">See also</span></span>

- [<span data-ttu-id="aee1f-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="aee1f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
