---
title: "ICorDebugInstanceFieldSymbol::GetName — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7071a640a5d3f379a03c45605cd6b3eb23c093ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="c98dc-102">ICorDebugInstanceFieldSymbol::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="c98dc-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="c98dc-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c98dc-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c98dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c98dc-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c98dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c98dc-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c98dc-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="c98dc-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c98dc-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="c98dc-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="c98dc-108">[out] Tablica znaków, która przechowuje nazwę zwrócony.</span><span class="sxs-lookup"><span data-stu-id="c98dc-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c98dc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c98dc-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c98dc-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c98dc-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c98dc-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c98dc-111">Requirements</span></span>  
 <span data-ttu-id="c98dc-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c98dc-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c98dc-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c98dc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c98dc-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c98dc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c98dc-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c98dc-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98dc-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c98dc-116">See Also</span></span>  
 [<span data-ttu-id="c98dc-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="c98dc-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="c98dc-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c98dc-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
