---
title: "ICorDebugValue3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3
helpviewer_keywords: ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3948a4c404036235767f8de6747966709b75bc4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="e9951-102">ICorDebugValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e9951-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="e9951-103">Rozszerza interfejsów "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę dla tablic, które są większe niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="e9951-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9951-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e9951-104">Methods</span></span>  
  
|<span data-ttu-id="e9951-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e9951-105">Method</span></span>|<span data-ttu-id="e9951-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e9951-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9951-107">GetSize64 — metoda</span><span class="sxs-lookup"><span data-stu-id="e9951-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="e9951-108">Pobiera rozmiar w bajtach to `ICorDebugValue3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="e9951-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9951-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9951-109">Remarks</span></span>  
 <span data-ttu-id="e9951-110">[ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda zwraca rozmiar obiektu zakresu od 0 do 2 147 483 647 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e9951-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="e9951-111">W [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], rozmiar tablic może być dłuższa niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="e9951-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="e9951-112">`ICorDebugValue3` Interfejs umożliwia określenie rozmiaru tych tablicach.</span><span class="sxs-lookup"><span data-stu-id="e9951-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9951-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9951-113">Requirements</span></span>  
 <span data-ttu-id="e9951-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9951-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9951-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9951-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9951-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9951-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9951-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9951-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9951-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9951-118">See Also</span></span>  
    
    
 [<span data-ttu-id="e9951-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e9951-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="e9951-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="e9951-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
