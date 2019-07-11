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
ms.openlocfilehash: 0d83f9c0b187ad8b2955bc12ff168e0c4f26b909
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765227"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="50c0f-102">ICorDebugThread4::GetBlockingObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="50c0f-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="50c0f-103">Zawiera wyliczenie uporządkowane [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur, które zapewniają blokowania informacje o wątku.</span><span class="sxs-lookup"><span data-stu-id="50c0f-103">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50c0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="50c0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50c0f-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="50c0f-106">[out] Wskaźnik do uporządkowanej wyliczenie [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="50c0f-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50c0f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50c0f-107">Remarks</span></span>  
 <span data-ttu-id="50c0f-108">Pierwszy element w wyliczeniu zwrócone odnosi się do pierwszego strukturę, która blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="50c0f-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="50c0f-109">Drugi element odnosi się do blokowania elementu, który występuje podczas uruchamiania wywołania asynchronicznego procedury (APC), gdy zablokowany w pierwszy i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="50c0f-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="50c0f-110">Wyliczenia jest prawidłowa tylko na czas trwania bieżącego stanu zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="50c0f-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="50c0f-111">Ta metoda musi zostać wywołana, gdy obiekt debugowany jest w stanie zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="50c0f-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="50c0f-112">Jeśli `ppBlockingObjectEnum` nie jest prawidłową wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="50c0f-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="50c0f-113">Jeśli wątek jest zablokowany i nie może być określony błąd, metoda zwraca wartość HRESULT, która wskazuje błąd; w przeciwnym razie zwraca wartość S_OK.</span><span class="sxs-lookup"><span data-stu-id="50c0f-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50c0f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50c0f-114">Requirements</span></span>  
 <span data-ttu-id="50c0f-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c0f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c0f-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50c0f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50c0f-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50c0f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50c0f-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c0f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c0f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50c0f-119">See also</span></span>

- [<span data-ttu-id="50c0f-120">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="50c0f-120">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="50c0f-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="50c0f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="50c0f-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="50c0f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
