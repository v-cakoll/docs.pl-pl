---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8b3b25c5e6e80b45ffc97e116c8649078f00861
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478716"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="05b6e-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="05b6e-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="05b6e-103">Pobiera nazwę załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="05b6e-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05b6e-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05b6e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05b6e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="05b6e-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="05b6e-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="05b6e-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="05b6e-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="05b6e-108">[out] Tablica znaków, które zawierają nazwy załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="05b6e-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05b6e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05b6e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b6e-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05b6e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b6e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05b6e-111">Requirements</span></span>  
 <span data-ttu-id="05b6e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05b6e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b6e-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05b6e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05b6e-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b6e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b6e-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b6e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b6e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05b6e-116">See also</span></span>
- [<span data-ttu-id="05b6e-117">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="05b6e-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="05b6e-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="05b6e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
