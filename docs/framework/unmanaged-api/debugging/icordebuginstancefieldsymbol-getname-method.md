---
title: ICorDebugInstanceFieldSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64357f873c9f125712fce33a1d9995c79a8cc006
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533458"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="01e01-102">ICorDebugInstanceFieldSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="01e01-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="01e01-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="01e01-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01e01-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01e01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01e01-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="01e01-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="01e01-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="01e01-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="01e01-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="01e01-108">[out] Tablica znaków, który przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="01e01-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01e01-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01e01-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01e01-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01e01-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e01-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01e01-111">Requirements</span></span>  
 <span data-ttu-id="01e01-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01e01-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e01-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01e01-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01e01-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01e01-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01e01-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e01-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e01-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01e01-116">See also</span></span>
- [<span data-ttu-id="01e01-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="01e01-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="01e01-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01e01-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
