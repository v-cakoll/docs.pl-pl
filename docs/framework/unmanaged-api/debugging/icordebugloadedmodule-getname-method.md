---
title: "ICorDebugLoadedModule::GetName — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aee475dfc425eea32ce4a1e5b4a081593574ba64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="e0c0b-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="e0c0b-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="e0c0b-103">Pobiera nazwę załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="e0c0b-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c0b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0c0b-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0c0b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0c0b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e0c0b-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="e0c0b-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e0c0b-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="e0c0b-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e0c0b-108">[out] Tablica znaków, które zawierają nazwę załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="e0c0b-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0c0b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0c0b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0c0b-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e0c0b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c0b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0c0b-111">Requirements</span></span>  
 <span data-ttu-id="e0c0b-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0c0b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0c0b-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0c0b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0c0b-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0c0b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0c0b-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0c0b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c0b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0c0b-116">See Also</span></span>  
 [<span data-ttu-id="e0c0b-117">Icordebugloadedmodule — interfejs</span><span class="sxs-lookup"><span data-stu-id="e0c0b-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="e0c0b-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e0c0b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
