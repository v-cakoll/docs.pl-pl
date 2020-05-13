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
ms.openlocfilehash: 366b5124cc66a4e9a1c3bd4e77f604f15ba8d8a8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379675"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="d98a6-102">ICorDebugThread4::GetBlockingObjects — Metoda</span><span class="sxs-lookup"><span data-stu-id="d98a6-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="d98a6-103">Udostępnia uporządkowane Wyliczenie struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) , które dostarczają informacje o blokowaniu wątku.</span><span class="sxs-lookup"><span data-stu-id="d98a6-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d98a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d98a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="d98a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d98a6-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="d98a6-106">określoną Wskaźnik do uporządkowanego wyliczania struktur [CorDebugBlockingObject](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="d98a6-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d98a6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d98a6-107">Remarks</span></span>  
 <span data-ttu-id="d98a6-108">Pierwszy element w zwracanym wyliczeniu odpowiada pierwszej strukturze, która blokuje wątek.</span><span class="sxs-lookup"><span data-stu-id="d98a6-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="d98a6-109">Drugi element odnosi się do bloku elementu, który jest napotkany podczas wykonywania wywołania procedury asynchronicznej (APC), gdy jest zablokowany w pierwszej i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d98a6-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="d98a6-110">Wyliczenie jest prawidłowe tylko dla czasu trwania bieżącego zsynchronizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="d98a6-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="d98a6-111">Ta metoda musi być wywoływana, gdy debugowanego obiektu jest w stanie zsynchronizowanym.</span><span class="sxs-lookup"><span data-stu-id="d98a6-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="d98a6-112">Jeśli `ppBlockingObjectEnum` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="d98a6-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="d98a6-113">Jeśli wątek jest zablokowany i nie można ustalić błędu, metoda zwraca wartość HRESULT, która wskazuje na błąd; w przeciwnym razie zwraca S_OK.</span><span class="sxs-lookup"><span data-stu-id="d98a6-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d98a6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d98a6-114">Requirements</span></span>  
 <span data-ttu-id="d98a6-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d98a6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d98a6-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d98a6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d98a6-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d98a6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d98a6-118">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d98a6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d98a6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d98a6-119">See also</span></span>

- [<span data-ttu-id="d98a6-120">ICorDebugThread4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d98a6-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="d98a6-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d98a6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d98a6-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d98a6-122">Debugging</span></span>](index.md)
