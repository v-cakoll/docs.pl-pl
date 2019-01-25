---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5ef73be22ea79d15ec53e8ab33c34441002acce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732430"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="e5287-102">ICorDebugLoadedModule::GetBaseAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="e5287-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="e5287-103">Pobiera adres podstawowy załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="e5287-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5287-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5287-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5287-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5287-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="e5287-106">[out] Wskaźnik do podstawowego adresu załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="e5287-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5287-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5287-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5287-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e5287-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5287-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5287-109">Requirements</span></span>  
 <span data-ttu-id="e5287-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5287-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5287-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5287-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5287-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5287-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5287-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5287-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5287-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5287-114">See also</span></span>
- [<span data-ttu-id="e5287-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5287-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="e5287-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e5287-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
