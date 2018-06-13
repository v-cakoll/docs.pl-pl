---
title: ICorDebugMergedAssemblyRecord::GetIndex — metoda
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0bcb5cdb4e93ae8ce6981bd86f125ecccb7d732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414839"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="b822a-102">ICorDebugMergedAssemblyRecord::GetIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="b822a-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="b822a-103">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="b822a-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b822a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b822a-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b822a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b822a-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="b822a-106">[out] Wskaźnik do indeksu prefiks.</span><span class="sxs-lookup"><span data-stu-id="b822a-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b822a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b822a-107">Remarks</span></span>  
 <span data-ttu-id="b822a-108">Indeks prefiks jest używany do chronienia konflikty nazw w nazwach typów scalonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="b822a-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b822a-109">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b822a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b822a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b822a-110">Requirements</span></span>  
 <span data-ttu-id="b822a-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b822a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b822a-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b822a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b822a-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b822a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b822a-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b822a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b822a-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b822a-115">See Also</span></span>  
 [<span data-ttu-id="b822a-116">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="b822a-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="b822a-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b822a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
