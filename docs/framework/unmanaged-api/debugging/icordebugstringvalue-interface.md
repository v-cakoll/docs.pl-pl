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
ms.openlocfilehash: d1d3a5eb6e0b24b40a35c13a99465dd3c7032a91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138944"
---
# <a name="icordebugstringvalue-interface"></a><span data-ttu-id="81a76-102">ICorDebugStringValue — Interfejs</span><span class="sxs-lookup"><span data-stu-id="81a76-102">ICorDebugStringValue Interface</span></span>
<span data-ttu-id="81a76-103">Podklasa elementu ICorDebugHeapValue, która ma zastosowanie do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="81a76-103">A subclass of ICorDebugHeapValue that applies to string values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81a76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="81a76-104">Methods</span></span>  
  
|<span data-ttu-id="81a76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="81a76-105">Method</span></span>|<span data-ttu-id="81a76-106">Opis</span><span class="sxs-lookup"><span data-stu-id="81a76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81a76-107">GetLength, metoda</span><span class="sxs-lookup"><span data-stu-id="81a76-107">GetLength Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|<span data-ttu-id="81a76-108">Pobiera liczbę znaków w ciągu, do których odwołuje się ten `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="81a76-108">Gets the number of characters in the string referenced by this `ICorDebugStringValue`.</span></span>|  
|[<span data-ttu-id="81a76-109">GetString, metoda</span><span class="sxs-lookup"><span data-stu-id="81a76-109">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|<span data-ttu-id="81a76-110">Pobiera ciąg, do którego odwołuje się ten `ICorDebugStringValue`.</span><span class="sxs-lookup"><span data-stu-id="81a76-110">Gets the string referenced by this `ICorDebugStringValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81a76-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81a76-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81a76-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="81a76-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81a76-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81a76-113">Requirements</span></span>  
 <span data-ttu-id="81a76-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81a76-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81a76-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81a76-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81a76-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81a76-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81a76-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81a76-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81a76-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81a76-118">See also</span></span>

- [<span data-ttu-id="81a76-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="81a76-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
