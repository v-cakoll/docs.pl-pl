---
title: "ICorDebugThread4::GetBlockingObjects — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread4.GetBlockingObjects Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6783d7f9af67acdff147cc46ea4f856f9b10bf3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="61ae9-102">ICorDebugThread4::GetBlockingObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="61ae9-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="61ae9-103">Udostępnia w kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur, które zapewniają blokowania informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="61ae9-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61ae9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61ae9-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61ae9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61ae9-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="61ae9-106">[out] Wskaźnik do kolejności wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="61ae9-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61ae9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61ae9-107">Remarks</span></span>  
 <span data-ttu-id="61ae9-108">Pierwszym elementem w wyliczeniu zwrócony odpowiada pierwszy struktury, która blokuje wątku.</span><span class="sxs-lookup"><span data-stu-id="61ae9-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="61ae9-109">Drugi element odnosi się do blokowania elementu, który jest napotkała podczas uruchamiania wywołanie asynchroniczne procedury (APC) w przypadku zablokowania pierwszego i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="61ae9-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="61ae9-110">Wyliczanie jest prawidłowa tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="61ae9-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="61ae9-111">Ta metoda musi zostać wywołany, gdy obiekt debugowany znajduje się w stanie zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="61ae9-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="61ae9-112">Jeśli `ppBlockingObjectEnum` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="61ae9-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="61ae9-113">Jeśli wątek został zablokowany i nie może być określony błąd, metoda zwraca wartość HRESULT, która wskazuje błąd; w przeciwnym razie zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="61ae9-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61ae9-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61ae9-114">Requirements</span></span>  
 <span data-ttu-id="61ae9-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61ae9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61ae9-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61ae9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61ae9-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61ae9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61ae9-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61ae9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61ae9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61ae9-119">See Also</span></span>  
 [<span data-ttu-id="61ae9-120">ICorDebugThread4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="61ae9-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="61ae9-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="61ae9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="61ae9-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="61ae9-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
