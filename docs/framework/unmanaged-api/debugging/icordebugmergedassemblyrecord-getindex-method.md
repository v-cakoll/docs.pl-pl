---
title: "ICorDebugMergedAssemblyRecord::GetIndex — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ff8d6935f5507ab02d9d566921cb7f8a890bb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="e55b8-102">ICorDebugMergedAssemblyRecord::GetIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="e55b8-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="e55b8-103">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="e55b8-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e55b8-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e55b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e55b8-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="e55b8-106">[out] Wskaźnik do indeksu prefiks.</span><span class="sxs-lookup"><span data-stu-id="e55b8-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e55b8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e55b8-107">Remarks</span></span>  
 <span data-ttu-id="e55b8-108">Indeks prefiks jest używany do chronienia konflikty nazw w nazwach typów scalonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="e55b8-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e55b8-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e55b8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e55b8-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e55b8-110">Requirements</span></span>  
 <span data-ttu-id="e55b8-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e55b8-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e55b8-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e55b8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e55b8-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e55b8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e55b8-114">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e55b8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55b8-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e55b8-115">See Also</span></span>  
 [<span data-ttu-id="e55b8-116">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="e55b8-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="e55b8-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e55b8-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
