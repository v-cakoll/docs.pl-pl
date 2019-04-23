---
title: ICorDebugInstanceFieldSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d23bf14fbb3d75534ac2d4a43eca0fbf3e994ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161398"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="33180-102">ICorDebugInstanceFieldSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="33180-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="33180-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="33180-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33180-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33180-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33180-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33180-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="33180-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="33180-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="33180-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="33180-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="33180-108">[out] Tablica znaków, który przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="33180-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33180-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33180-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33180-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="33180-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33180-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33180-111">Requirements</span></span>  
 <span data-ttu-id="33180-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33180-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33180-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33180-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33180-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33180-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33180-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33180-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33180-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33180-116">See also</span></span>

- [<span data-ttu-id="33180-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="33180-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="33180-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="33180-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
