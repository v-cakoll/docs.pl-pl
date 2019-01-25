---
title: ICorDebugStaticFieldSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6da390fb7de3c248fa5389f133d65f9914d5260a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714707"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="6ce18-102">ICorDebugStaticFieldSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="6ce18-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="6ce18-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="6ce18-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ce18-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ce18-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6ce18-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6ce18-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="6ce18-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6ce18-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="6ce18-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6ce18-108">[out] Tablica znaków, który przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="6ce18-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ce18-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ce18-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ce18-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6ce18-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ce18-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ce18-111">Requirements</span></span>  
 <span data-ttu-id="6ce18-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ce18-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ce18-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ce18-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ce18-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ce18-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ce18-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ce18-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce18-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ce18-116">See also</span></span>
- [<span data-ttu-id="6ce18-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ce18-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="6ce18-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6ce18-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
