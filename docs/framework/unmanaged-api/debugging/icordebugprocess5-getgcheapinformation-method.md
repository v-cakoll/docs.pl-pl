---
title: ICorDebugProcess5::GetGCHeapInformation — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 62d45da44a95eae399fbbd287aa997a5f913d0b0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209659"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="dee72-102">ICorDebugProcess5::GetGCHeapInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="dee72-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="dee72-103">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy jest obecnie wyliczalne.</span><span class="sxs-lookup"><span data-stu-id="dee72-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dee72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dee72-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dee72-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dee72-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="dee72-106">określoną Wskaźnik do wartości [COR_HEAPINFO](cor-heapinfo-structure.md) , która zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dee72-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dee72-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dee72-107">Remarks</span></span>  
 <span data-ttu-id="dee72-108">`ICorDebugProcess5::GetGCHeapInformation`Metoda musi zostać wywołana przed wyliczeniem sterty lub poszczególnych regionów sterty, aby upewnić się, że struktury wyrzucania elementów bezużytecznych w procesie są obecnie prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="dee72-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="dee72-109">Nie można przeprowadzić sterty odzyskiwania pamięci, gdy kolekcja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="dee72-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="dee72-110">W przeciwnym razie Wyliczenie może przechwytywać nieprawidłowe struktury wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dee72-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dee72-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dee72-111">Requirements</span></span>  
 <span data-ttu-id="dee72-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dee72-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dee72-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dee72-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dee72-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dee72-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dee72-115">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dee72-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dee72-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dee72-116">See also</span></span>

- [<span data-ttu-id="dee72-117">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dee72-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="dee72-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="dee72-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
