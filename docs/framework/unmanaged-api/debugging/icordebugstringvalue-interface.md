---
title: ICorDebugStringValue — Interfejs
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
ms.openlocfilehash: cff85a77b113440c2274910cae8ef93419d1bc1b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965361"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="b72d2-102">ICorDebugStringValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b72d2-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="b72d2-103">Podklasa klasy ICorDebugHeapValue, która odnosi się do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="b72d2-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b72d2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b72d2-104">Methods</span></span>  
  
|<span data-ttu-id="b72d2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b72d2-105">Method</span></span>|<span data-ttu-id="b72d2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b72d2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b72d2-107">GetLength, metoda</span><span class="sxs-lookup"><span data-stu-id="b72d2-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="b72d2-108">Pobiera liczbę znaków w ciągu przywoływane przez to `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="b72d2-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="b72d2-109">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="b72d2-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="b72d2-110">Pobiera ciąg przywoływane przez to `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="b72d2-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b72d2-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b72d2-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b72d2-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="b72d2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b72d2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b72d2-113">Requirements</span></span>  
 <span data-ttu-id="b72d2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b72d2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b72d2-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b72d2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b72d2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b72d2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b72d2-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b72d2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b72d2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b72d2-118">See also</span></span>
- [<span data-ttu-id="b72d2-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b72d2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
