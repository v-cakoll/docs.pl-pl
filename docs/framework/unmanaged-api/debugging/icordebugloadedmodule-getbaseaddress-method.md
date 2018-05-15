---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c12ea84f1a706850972b2e404ec52eea3523de7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="77d71-102">ICorDebugLoadedModule::GetBaseAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="77d71-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="77d71-103">Pobiera adres podstawowy załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="77d71-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d71-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77d71-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77d71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77d71-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="77d71-106">[out] Wskaźnik do adres podstawowy załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="77d71-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77d71-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77d71-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77d71-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="77d71-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d71-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77d71-109">Requirements</span></span>  
 <span data-ttu-id="77d71-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77d71-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77d71-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77d71-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77d71-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77d71-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77d71-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77d71-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d71-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77d71-114">See Also</span></span>  
 [<span data-ttu-id="77d71-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="77d71-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="77d71-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="77d71-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
