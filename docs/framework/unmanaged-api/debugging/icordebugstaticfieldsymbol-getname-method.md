---
title: ICorDebugStaticFieldSymbol::GetName Method
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5f52999c3f680fbccefe4681f83d473cdb86306
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206489"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="5c0ad-102">ICorDebugStaticFieldSymbol::GetName Method</span><span class="sxs-lookup"><span data-stu-id="5c0ad-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="5c0ad-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="5c0ad-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c0ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c0ad-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c0ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c0ad-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5c0ad-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="5c0ad-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5c0ad-107">[out] Wskaźnik do liczby znaków rzeczywiście zapisanych na `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="5c0ad-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5c0ad-108">[out] Tablica znaków, który przechowuje nazwę zwracanego.</span><span class="sxs-lookup"><span data-stu-id="5c0ad-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c0ad-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c0ad-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c0ad-110">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5c0ad-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c0ad-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c0ad-111">Requirements</span></span>  
 <span data-ttu-id="5c0ad-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c0ad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c0ad-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c0ad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c0ad-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c0ad-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5c0ad-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5c0ad-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5c0ad-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c0ad-116">See also</span></span>

- [<span data-ttu-id="5c0ad-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c0ad-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="5c0ad-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5c0ad-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
