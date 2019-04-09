---
title: ICorDebugInstanceFieldSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d23bf14fbb3d75534ac2d4a43eca0fbf3e994ae
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161398"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="e797d-102">ICorDebugInstanceFieldSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="e797d-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="e797d-103">Pobiera nazwę pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e797d-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e797d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e797d-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e797d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e797d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e797d-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="e797d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e797d-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="e797d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="e797d-108">[out] Tablica znaków, który przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="e797d-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e797d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e797d-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e797d-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e797d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e797d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e797d-111">Requirements</span></span>  
 <span data-ttu-id="e797d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e797d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e797d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e797d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e797d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e797d-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e797d-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e797d-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e797d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e797d-116">See also</span></span>

- [<span data-ttu-id="e797d-117">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="e797d-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="e797d-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e797d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
