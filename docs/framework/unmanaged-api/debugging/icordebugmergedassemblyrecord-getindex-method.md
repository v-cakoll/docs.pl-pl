---
title: 'ICorDebugMergedAssemblyRecord:: getIndex — Metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: 236bd8b22d6c3ec783d787f6c906ede3193cfc1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131406"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="73675-102">ICorDebugMergedAssemblyRecord:: getIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="73675-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="73675-103">Pobiera indeks prefiksu zestawu.</span><span class="sxs-lookup"><span data-stu-id="73675-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73675-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73675-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73675-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73675-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="73675-106">określoną Wskaźnik do indeksu prefiksu.</span><span class="sxs-lookup"><span data-stu-id="73675-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73675-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73675-107">Remarks</span></span>  
 <span data-ttu-id="73675-108">Indeks prefiksu służy do zapobiegania kolizjom nazw w scalonych nazwach typów metadanych.</span><span class="sxs-lookup"><span data-stu-id="73675-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73675-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="73675-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73675-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73675-110">Requirements</span></span>  
 <span data-ttu-id="73675-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73675-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73675-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73675-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73675-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73675-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73675-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73675-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73675-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73675-115">See also</span></span>

- [<span data-ttu-id="73675-116">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="73675-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="73675-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="73675-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
