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
ms.openlocfilehash: 703f159c5bc6b73dcd0e770bdeb61f676aae034c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792381"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="406e3-102">ICorDebugProcess5::GetGCHeapInformation — Metoda</span><span class="sxs-lookup"><span data-stu-id="406e3-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>
<span data-ttu-id="406e3-103">Zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych, w tym o tym, czy jest obecnie wyliczalne.</span><span class="sxs-lookup"><span data-stu-id="406e3-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="406e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="406e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="406e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="406e3-105">Parameters</span></span>  
 `pHeapInfo`  
 <span data-ttu-id="406e3-106">określoną Wskaźnik do wartości [COR_HEAPINFO](cor-heapinfo-structure.md) , która zawiera ogólne informacje o stercie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="406e3-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="406e3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="406e3-107">Remarks</span></span>  
 <span data-ttu-id="406e3-108">Metodę `ICorDebugProcess5::GetGCHeapInformation` należy wywołać przed wyliczeniem sterty lub poszczególnych regionów sterty, aby upewnić się, że struktury wyrzucania elementów bezużytecznych w procesie są obecnie prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="406e3-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="406e3-109">Nie można przeprowadzić sterty odzyskiwania pamięci, gdy kolekcja jest w toku.</span><span class="sxs-lookup"><span data-stu-id="406e3-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="406e3-110">W przeciwnym razie Wyliczenie może przechwytywać nieprawidłowe struktury wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="406e3-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="406e3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="406e3-111">Requirements</span></span>  
 <span data-ttu-id="406e3-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="406e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="406e3-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="406e3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="406e3-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="406e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="406e3-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="406e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="406e3-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="406e3-116">See also</span></span>

- [<span data-ttu-id="406e3-117">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="406e3-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="406e3-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="406e3-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
