---
title: ICorDebugValue3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300d2263c076c9028340863e2f7a3fa27a36ef9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993736"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="8a93a-102">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8a93a-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="8a93a-103">Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="8a93a-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a93a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8a93a-104">Methods</span></span>  
  
|<span data-ttu-id="8a93a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8a93a-105">Method</span></span>|<span data-ttu-id="8a93a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8a93a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a93a-107">GetSize64, metoda</span><span class="sxs-lookup"><span data-stu-id="8a93a-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="8a93a-108">Pobiera rozmiar w bajtach to `ICorDebugValue3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8a93a-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a93a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a93a-109">Remarks</span></span>  
 <span data-ttu-id="8a93a-110">[ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda zwraca rozmiar obiektu, z zakresu od 0 do 2 147 483 647 bajtów.</span><span class="sxs-lookup"><span data-stu-id="8a93a-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="8a93a-111">W [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], rozmiar macierzy będą mogli przekraczać 2 GB.</span><span class="sxs-lookup"><span data-stu-id="8a93a-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="8a93a-112">`ICorDebugValue3` Interfejsu pozwala określić rozmiar macierzy.</span><span class="sxs-lookup"><span data-stu-id="8a93a-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a93a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a93a-113">Requirements</span></span>  
 <span data-ttu-id="8a93a-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a93a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a93a-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a93a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a93a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a93a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a93a-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a93a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a93a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a93a-118">See also</span></span>

- [<span data-ttu-id="8a93a-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8a93a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a93a-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8a93a-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
