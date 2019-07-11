---
title: ICorDebugLoadedModule::GetName — metoda
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5b3889829ced876b23ea6632f35f4da6beffdca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759924"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="ef343-102">ICorDebugLoadedModule::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="ef343-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="ef343-103">Pobiera nazwę załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="ef343-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef343-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef343-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef343-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef343-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="ef343-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="ef343-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ef343-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="ef343-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ef343-108">[out] Tablica znaków, które zawierają nazwy załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="ef343-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef343-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef343-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ef343-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ef343-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef343-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef343-111">Requirements</span></span>  
 <span data-ttu-id="ef343-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef343-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef343-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef343-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef343-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef343-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef343-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef343-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef343-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef343-116">See also</span></span>

- [<span data-ttu-id="ef343-117">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef343-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ef343-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ef343-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
