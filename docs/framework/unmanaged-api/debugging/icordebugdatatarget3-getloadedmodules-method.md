---
title: ICorDebugDataTarget3::GetLoadedModules — metoda
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 120b839b2b11c85f42bb1a0ae4701de0dea33879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912822"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="c605f-102">ICorDebugDataTarget3::GetLoadedModules — metoda</span><span class="sxs-lookup"><span data-stu-id="c605f-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="c605f-103">Pobiera listę modułów, które zostały wcześniej załadowane.</span><span class="sxs-lookup"><span data-stu-id="c605f-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c605f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c605f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c605f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c605f-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="c605f-106">podczas Liczba modułów, dla których żądane są informacje.</span><span class="sxs-lookup"><span data-stu-id="c605f-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="c605f-107">określoną Wskaźnik do liczby modułów, na których zwrócono informacje.</span><span class="sxs-lookup"><span data-stu-id="c605f-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="c605f-108">określoną Wskaźnik do tablicy obiektów [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) , które zawierają informacje o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="c605f-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c605f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c605f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c605f-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c605f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c605f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c605f-111">Requirements</span></span>  
 <span data-ttu-id="c605f-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c605f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c605f-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c605f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c605f-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c605f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c605f-115">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c605f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c605f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c605f-116">See also</span></span>

- [<span data-ttu-id="c605f-117">ICorDebugDataTarget3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c605f-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="c605f-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c605f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
