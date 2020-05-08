---
title: ICorDebugDataTarget3::GetLoadedModules — metoda
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: c3565f4f9284bc121b0e2d3b0885cbea927acfdd
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976424"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="5c5d5-102">ICorDebugDataTarget3::GetLoadedModules — metoda</span><span class="sxs-lookup"><span data-stu-id="5c5d5-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="5c5d5-103">Pobiera listę modułów, które zostały wcześniej załadowane.</span><span class="sxs-lookup"><span data-stu-id="5c5d5-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c5d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c5d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c5d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c5d5-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="5c5d5-106">podczas Liczba modułów, dla których żądane są informacje.</span><span class="sxs-lookup"><span data-stu-id="5c5d5-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="5c5d5-107">określoną Wskaźnik do liczby modułów, na których zwrócono informacje.</span><span class="sxs-lookup"><span data-stu-id="5c5d5-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="5c5d5-108">określoną Wskaźnik do tablicy obiektów [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) , które zawierają informacje o załadowanych modułach.</span><span class="sxs-lookup"><span data-stu-id="5c5d5-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c5d5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c5d5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c5d5-110">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5c5d5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c5d5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c5d5-111">Requirements</span></span>  
 <span data-ttu-id="5c5d5-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c5d5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c5d5-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c5d5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c5d5-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5c5d5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c5d5-115">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c5d5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5d5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c5d5-116">See also</span></span>

- [<span data-ttu-id="5c5d5-117">ICorDebugDataTarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="5c5d5-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="5c5d5-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c5d5-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
