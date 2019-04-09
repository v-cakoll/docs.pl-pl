---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4601261971cce32b6d6d9ee7377f725a85103a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183472"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="70d37-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="70d37-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="70d37-103">Pobiera rozmiar w bajtach załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="70d37-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70d37-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70d37-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70d37-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70d37-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="70d37-106">[out] Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="70d37-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70d37-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70d37-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70d37-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="70d37-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70d37-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70d37-109">Requirements</span></span>  
 <span data-ttu-id="70d37-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70d37-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70d37-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70d37-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70d37-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70d37-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="70d37-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="70d37-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70d37-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70d37-114">See also</span></span>

- [<span data-ttu-id="70d37-115">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="70d37-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="70d37-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="70d37-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
