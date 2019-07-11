---
title: ICorDebugStaticFieldSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01281e09533ba7196d3fa3e57c463636cfb0dd77
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760834"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="84b31-102">ICorDebugStaticFieldSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="84b31-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="84b31-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="84b31-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84b31-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84b31-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84b31-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84b31-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="84b31-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="84b31-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="84b31-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="84b31-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="84b31-108">[out] Tablica znaków, który przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="84b31-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84b31-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84b31-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84b31-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84b31-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84b31-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84b31-111">Requirements</span></span>  
 <span data-ttu-id="84b31-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84b31-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84b31-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84b31-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84b31-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84b31-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84b31-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84b31-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b31-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84b31-116">See also</span></span>

- [<span data-ttu-id="84b31-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="84b31-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="84b31-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="84b31-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
