---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9768fb91749158bf3193919b2106bde1c618468a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413234"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="01fe1-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="01fe1-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="01fe1-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="01fe1-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01fe1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01fe1-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01fe1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01fe1-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="01fe1-106">[out] Wskaźnik do liczba bajtów w module załadowany.</span><span class="sxs-lookup"><span data-stu-id="01fe1-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01fe1-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01fe1-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01fe1-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01fe1-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01fe1-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01fe1-109">Requirements</span></span>  
 <span data-ttu-id="01fe1-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01fe1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01fe1-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01fe1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01fe1-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01fe1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01fe1-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01fe1-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01fe1-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01fe1-114">See Also</span></span>  
 [<span data-ttu-id="01fe1-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="01fe1-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="01fe1-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01fe1-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
