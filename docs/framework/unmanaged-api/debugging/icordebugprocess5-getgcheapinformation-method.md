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
ms.openlocfilehash: 3aa9fe884b16a239f5105dd262edeb8fc3e4abaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084403"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="1c3d9-102">ICorDebugProcess5::GetGCHeapInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="1c3d9-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="1c3d9-103">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy jest obecnie wyliczalne.</span><span class="sxs-lookup"><span data-stu-id="1c3d9-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c3d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c3d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c3d9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1c3d9-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="1c3d9-106">określoną Wskaźnik do wartości [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) , która zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1c3d9-106">[out] A pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c3d9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c3d9-107">Remarks</span></span>  
 <span data-ttu-id="1c3d9-108">Metodę `ICorDebugProcess5::GetGCHeapInformation` należy wywołać przed wyliczeniem sterty lub poszczególnych regionów sterty, aby upewnić się, że struktury wyrzucania elementów bezużytecznych w procesie są obecnie prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="1c3d9-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="1c3d9-109">Nie można przeprowadzić sterty odzyskiwania pamięci, gdy kolekcja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="1c3d9-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="1c3d9-110">W przeciwnym razie Wyliczenie może przechwytywać nieprawidłowe struktury wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1c3d9-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c3d9-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c3d9-111">Requirements</span></span>  
 <span data-ttu-id="1c3d9-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c3d9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c3d9-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1c3d9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c3d9-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1c3d9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c3d9-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c3d9-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c3d9-116">See also</span></span>

- [<span data-ttu-id="1c3d9-117">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c3d9-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="1c3d9-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1c3d9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
