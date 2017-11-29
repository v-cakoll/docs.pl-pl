---
title: "ICorDebugDataTarget3::GetLoadedModules — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc4820d2c71830b297ed690c440c90cfff1f9601
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="72532-102">ICorDebugDataTarget3::GetLoadedModules — metoda</span><span class="sxs-lookup"><span data-stu-id="72532-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="72532-103">Pobiera listę modułów, które zostały załadowane do tej pory.</span><span class="sxs-lookup"><span data-stu-id="72532-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72532-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72532-104">Syntax</span></span>  
  
```  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72532-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72532-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="72532-106">[in] Liczba modułów, dla których jest wymagane informacje.</span><span class="sxs-lookup"><span data-stu-id="72532-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="72532-107">[out] Wskaźnik do liczby modułów, o których informacje zwrócone.</span><span class="sxs-lookup"><span data-stu-id="72532-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="72532-108">[out] Wskaźnik do tablicy [icordebugloadedmodule —](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) obiektów, które zawierają informacje o załadowanych modułów.</span><span class="sxs-lookup"><span data-stu-id="72532-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72532-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72532-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72532-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="72532-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72532-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72532-111">Requirements</span></span>  
 <span data-ttu-id="72532-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72532-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72532-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72532-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72532-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72532-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72532-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72532-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72532-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72532-116">See Also</span></span>  
 [<span data-ttu-id="72532-117">Icordebugdatatarget3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="72532-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 [<span data-ttu-id="72532-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="72532-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
