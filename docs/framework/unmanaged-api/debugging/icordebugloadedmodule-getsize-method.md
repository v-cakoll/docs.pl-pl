---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946253"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="6d3a4-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="6d3a4-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="6d3a4-103">Pobiera rozmiar w bajtach załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="6d3a4-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d3a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d3a4-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d3a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d3a4-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="6d3a4-106">[out] Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="6d3a4-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d3a4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d3a4-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d3a4-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d3a4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d3a4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d3a4-109">Requirements</span></span>  
 <span data-ttu-id="6d3a4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d3a4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d3a4-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d3a4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d3a4-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d3a4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d3a4-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d3a4-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3a4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d3a4-114">See also</span></span>

- [<span data-ttu-id="6d3a4-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d3a4-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="6d3a4-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d3a4-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
