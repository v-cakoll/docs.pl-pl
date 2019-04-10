---
title: ICorDebugMergedAssemblyRecord::GetIndex Method
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8ba470325098125aee8ef7de01fa6aa70596d42
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202602"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="180d2-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span><span class="sxs-lookup"><span data-stu-id="180d2-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="180d2-103">Pobiera indeks prefiks zestawu.</span><span class="sxs-lookup"><span data-stu-id="180d2-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="180d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="180d2-104">Syntax</span></span>  
  
```  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="180d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="180d2-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="180d2-106">[out] Wskaźnik do indeksu prefiks.</span><span class="sxs-lookup"><span data-stu-id="180d2-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="180d2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="180d2-107">Remarks</span></span>  
 <span data-ttu-id="180d2-108">Indeks prefiks jest używany aby zapobiec kolizjom nazw w nazwach typów scalonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="180d2-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="180d2-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="180d2-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="180d2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="180d2-110">Requirements</span></span>  
 <span data-ttu-id="180d2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="180d2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="180d2-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="180d2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="180d2-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="180d2-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="180d2-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="180d2-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="180d2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="180d2-115">See also</span></span>

- [<span data-ttu-id="180d2-116">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="180d2-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="180d2-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="180d2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
