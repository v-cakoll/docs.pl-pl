---
title: ICorDebugThread4::GetBlockingObjects — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93cae803b42d80dc0f868e2189de442eedea43f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186371"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="3ff93-102">ICorDebugThread4::GetBlockingObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ff93-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="3ff93-103">Zawiera wyliczenie uporządkowane [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur, które zapewniają blokowania informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="3ff93-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ff93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ff93-104">Syntax</span></span>  
  
```  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ff93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ff93-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="3ff93-106">[out] Wskaźnik do uporządkowanej wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="3ff93-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ff93-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ff93-107">Remarks</span></span>  
 <span data-ttu-id="3ff93-108">Pierwszy element w wyliczeniu zwrócone odnosi się do pierwszego strukturę, która blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="3ff93-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="3ff93-109">Drugi element odnosi się do blokowania elementu, który występuje podczas uruchamiania wywołania asynchronicznego procedury (APC), gdy zablokowany w pierwszy i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3ff93-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="3ff93-110">Wyliczenia jest prawidłowa tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="3ff93-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="3ff93-111">Ta metoda musi zostać wywołana, gdy obiekt debugowany jest w stanie zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="3ff93-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="3ff93-112">Jeśli `ppBlockingObjectEnum` nie jest prawidłową wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="3ff93-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="3ff93-113">Jeśli wątek jest zablokowany i nie może być określony błąd, metoda zwraca wartość HRESULT, która wskazuje błąd; w przeciwnym razie zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="3ff93-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ff93-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ff93-114">Requirements</span></span>  
 <span data-ttu-id="3ff93-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ff93-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ff93-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ff93-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ff93-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ff93-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3ff93-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3ff93-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3ff93-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ff93-119">See also</span></span>

- [<span data-ttu-id="3ff93-120">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3ff93-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="3ff93-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3ff93-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3ff93-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3ff93-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
