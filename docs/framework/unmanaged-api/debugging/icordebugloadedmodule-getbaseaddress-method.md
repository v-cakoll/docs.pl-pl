---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85748106edb34b98f975a40bcc2617401536e271
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910101"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="43771-102">ICorDebugLoadedModule::GetBaseAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="43771-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="43771-103">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="43771-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43771-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43771-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43771-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="43771-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="43771-106">określoną Wskaźnik na adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="43771-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43771-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43771-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43771-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="43771-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43771-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43771-109">Requirements</span></span>  
 <span data-ttu-id="43771-110">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43771-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43771-111">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43771-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43771-112">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43771-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43771-113">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43771-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43771-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43771-114">See also</span></span>

- [<span data-ttu-id="43771-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="43771-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="43771-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="43771-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
