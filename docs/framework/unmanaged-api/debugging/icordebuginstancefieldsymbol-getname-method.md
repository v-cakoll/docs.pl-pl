---
title: ICorDebugInstanceFieldSymbol::GetName — metoda
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bcd5a2735a77813436ea4796a27003f4cb140c7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423482"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="995f6-102">ICorDebugInstanceFieldSymbol::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="995f6-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="995f6-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="995f6-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="995f6-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="995f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="995f6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="995f6-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="995f6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="995f6-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="995f6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="995f6-108">[out] Tablica znaków, która przechowuje nazwę zwrócony.</span><span class="sxs-lookup"><span data-stu-id="995f6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="995f6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="995f6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="995f6-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="995f6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="995f6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="995f6-111">Requirements</span></span>  
 <span data-ttu-id="995f6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="995f6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="995f6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="995f6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="995f6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="995f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="995f6-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="995f6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995f6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="995f6-116">See Also</span></span>  
 [<span data-ttu-id="995f6-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="995f6-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="995f6-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="995f6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
