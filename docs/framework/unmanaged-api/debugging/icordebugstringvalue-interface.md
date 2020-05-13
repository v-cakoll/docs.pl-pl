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
ms.openlocfilehash: 5537a48fd085ce98de855fa1ec0913e2637e58e0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376195"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="6bcb7-102">ICorDebugStringValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="6bcb7-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="6bcb7-103">Podklasa elementu ICorDebugHeapValue, która ma zastosowanie do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="6bcb7-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bcb7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6bcb7-104">Methods</span></span>  
  
|<span data-ttu-id="6bcb7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6bcb7-105">Method</span></span>|<span data-ttu-id="6bcb7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6bcb7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bcb7-107">GetLength, metoda</span><span class="sxs-lookup"><span data-stu-id="6bcb7-107">GetLength Method</span></span>](icordebugstringvalue-getlength-method.md)|<span data-ttu-id="6bcb7-108">Pobiera liczbę znaków w ciągu, do którego się odwołuje `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="6bcb7-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="6bcb7-109">GetString — Metoda</span><span class="sxs-lookup"><span data-stu-id="6bcb7-109">GetString Method</span></span>](icordebugstringvalue-getstring-method.md)|<span data-ttu-id="6bcb7-110">Pobiera ciąg, do którego się odwołuje `ICorDebugStringValue` .</span><span class="sxs-lookup"><span data-stu-id="6bcb7-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bcb7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bcb7-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bcb7-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6bcb7-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bcb7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6bcb7-113">Requirements</span></span>  
 <span data-ttu-id="6bcb7-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bcb7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bcb7-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bcb7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bcb7-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6bcb7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bcb7-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bcb7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcb7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bcb7-118">See also</span></span>

- [<span data-ttu-id="6bcb7-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6bcb7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
