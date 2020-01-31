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
ms.openlocfilehash: 39833b689f28437b4241d9cb15fb4a92b2f9bcc3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791372"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="8b7e7-102">ICorDebugThread4::GetBlockingObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b7e7-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="8b7e7-103">Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b7e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b7e7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b7e7-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="8b7e7-106">określoną Wskaźnik do uporządkowanego wyliczania struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="8b7e7-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b7e7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b7e7-107">Remarks</span></span>  
 <span data-ttu-id="8b7e7-108">Pierwszy element w zwracanym wyliczeniu odpowiada pierwszej strukturze, która blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="8b7e7-109">Drugi element odnosi się do bloku elementu, który jest napotkany podczas wykonywania wywołania procedury asynchronicznej (APC), gdy jest zablokowany w pierwszej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="8b7e7-110">Wyliczenie jest prawidłowe tylko dla czasu trwania bieżącego zsynchronizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="8b7e7-111">Ta metoda musi być wywoływana, gdy debugowanego obiektu jest w stanie zsynchronizowanym.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="8b7e7-112">Jeśli `ppBlockingObjectEnum` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="8b7e7-113">Jeśli wątek jest zablokowany i nie można ustalić błędu, metoda zwraca wartość HRESULT, która wskazuje na błąd; w przeciwnym razie zwraca S_OK.</span><span class="sxs-lookup"><span data-stu-id="8b7e7-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b7e7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b7e7-114">Requirements</span></span>  
 <span data-ttu-id="8b7e7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b7e7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b7e7-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8b7e7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b7e7-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8b7e7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b7e7-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7e7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b7e7-119">See also</span></span>

- [<span data-ttu-id="8b7e7-120">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b7e7-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="8b7e7-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8b7e7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8b7e7-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8b7e7-122">Debugging</span></span>](index.md)
