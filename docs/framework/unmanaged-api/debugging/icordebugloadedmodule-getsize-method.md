---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3067cdee1d3a5df0ad5594bce581139431fd1846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936874"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="f0e2e-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="f0e2e-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="f0e2e-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="f0e2e-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0e2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0e2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0e2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0e2e-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="f0e2e-106">określoną Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="f0e2e-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0e2e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0e2e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0e2e-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0e2e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0e2e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0e2e-109">Requirements</span></span>  
 <span data-ttu-id="f0e2e-110">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0e2e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0e2e-111">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0e2e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0e2e-112">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0e2e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0e2e-113">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0e2e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e2e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0e2e-114">See also</span></span>

- [<span data-ttu-id="f0e2e-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0e2e-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="f0e2e-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0e2e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
