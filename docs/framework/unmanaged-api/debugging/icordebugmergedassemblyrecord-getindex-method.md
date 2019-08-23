---
title: 'ICorDebugMergedAssemblyRecord:: getIndex — Metoda'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca304b90cee291ef86e225c2b0691631833e53a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917948"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="be097-102">ICorDebugMergedAssemblyRecord:: getIndex — Metoda</span><span class="sxs-lookup"><span data-stu-id="be097-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="be097-103">Pobiera indeks prefiksu zestawu.</span><span class="sxs-lookup"><span data-stu-id="be097-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be097-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be097-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be097-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be097-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="be097-106">określoną Wskaźnik do indeksu prefiksu.</span><span class="sxs-lookup"><span data-stu-id="be097-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be097-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be097-107">Remarks</span></span>  
 <span data-ttu-id="be097-108">Indeks prefiksu służy do zapobiegania kolizjom nazw w scalonych nazwach typów metadanych.</span><span class="sxs-lookup"><span data-stu-id="be097-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be097-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="be097-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be097-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be097-110">Requirements</span></span>  
 <span data-ttu-id="be097-111">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be097-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be097-112">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be097-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be097-113">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be097-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be097-114">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be097-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be097-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be097-115">See also</span></span>

- [<span data-ttu-id="be097-116">ICorDebugMergedAssemblyRecord, interfejs</span><span class="sxs-lookup"><span data-stu-id="be097-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="be097-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="be097-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
