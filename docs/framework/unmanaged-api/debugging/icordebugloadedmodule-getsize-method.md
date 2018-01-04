---
title: "ICorDebugLoadedModule::GetSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1fb340845afac0f5a13f7c4646d11ac057ebd054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="9b5b8-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="9b5b8-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="9b5b8-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="9b5b8-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b5b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b5b8-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b5b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b5b8-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="9b5b8-106">[out] Wskaźnik do liczba bajtów w module załadowany.</span><span class="sxs-lookup"><span data-stu-id="9b5b8-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b5b8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b5b8-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b5b8-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b5b8-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b5b8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b5b8-109">Requirements</span></span>  
 <span data-ttu-id="9b5b8-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b5b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b5b8-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b5b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b5b8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b5b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b5b8-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b5b8-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5b8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b5b8-114">See Also</span></span>  
 [<span data-ttu-id="9b5b8-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b5b8-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="9b5b8-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9b5b8-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
