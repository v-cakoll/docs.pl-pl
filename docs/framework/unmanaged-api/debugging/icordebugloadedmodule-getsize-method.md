---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4c4888419bb13db43a4a15d98965cc8d3cb8e77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515582"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="be7d2-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="be7d2-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="be7d2-103">Pobiera rozmiar w bajtach załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="be7d2-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be7d2-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be7d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be7d2-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="be7d2-106">[out] Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="be7d2-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be7d2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be7d2-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be7d2-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="be7d2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be7d2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be7d2-109">Requirements</span></span>  
 <span data-ttu-id="be7d2-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be7d2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be7d2-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be7d2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be7d2-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be7d2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be7d2-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be7d2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7d2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be7d2-114">See also</span></span>
- [<span data-ttu-id="be7d2-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="be7d2-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="be7d2-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="be7d2-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
