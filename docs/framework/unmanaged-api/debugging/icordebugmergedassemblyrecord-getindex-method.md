---
title: ICorDebugMergedAssemblyRecord::GetIndex Method
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8ba470325098125aee8ef7de01fa6aa70596d42
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202602"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="c552d-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span><span class="sxs-lookup"><span data-stu-id="c552d-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="c552d-103">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="c552d-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c552d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c552d-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c552d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c552d-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="c552d-106">[out] Wskaźnik do indeksu prefiks.</span><span class="sxs-lookup"><span data-stu-id="c552d-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c552d-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c552d-107">Remarks</span></span>  
 <span data-ttu-id="c552d-108">Indeks prefiks jest używany aby zapobiec kolizjom nazw w nazwach typów scalonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="c552d-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c552d-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c552d-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c552d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c552d-110">Requirements</span></span>  
 <span data-ttu-id="c552d-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c552d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c552d-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c552d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c552d-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c552d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c552d-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c552d-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c552d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c552d-115">See also</span></span>

- [<span data-ttu-id="c552d-116">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="c552d-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="c552d-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c552d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
