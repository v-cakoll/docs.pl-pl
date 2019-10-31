---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 8af814ff2eaaf3ae6dae9031c13bf37ea0c1236b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122656"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="c1b52-102">ICorDebugLoadedModule::GetBaseAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="c1b52-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="c1b52-103">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="c1b52-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1b52-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1b52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1b52-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="c1b52-106">określoną Wskaźnik na adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="c1b52-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1b52-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1b52-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1b52-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c1b52-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b52-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1b52-109">Requirements</span></span>  
 <span data-ttu-id="c1b52-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b52-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b52-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c1b52-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1b52-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c1b52-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1b52-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b52-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b52-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1b52-114">See also</span></span>

- [<span data-ttu-id="c1b52-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1b52-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="c1b52-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c1b52-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
