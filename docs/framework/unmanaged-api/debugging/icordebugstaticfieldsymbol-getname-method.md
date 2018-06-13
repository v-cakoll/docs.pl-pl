---
title: ICorDebugStaticFieldSymbol::GetName — metoda
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095c84a5cb448803bbfa45e0fad8a494343ca7f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422321"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="a7eca-102">ICorDebugStaticFieldSymbol::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="a7eca-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="a7eca-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="a7eca-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7eca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7eca-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7eca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7eca-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a7eca-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="a7eca-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a7eca-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="a7eca-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a7eca-108">[out] Tablica znaków, która przechowuje nazwę zwrócony.</span><span class="sxs-lookup"><span data-stu-id="a7eca-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7eca-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7eca-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7eca-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a7eca-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7eca-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7eca-111">Requirements</span></span>  
 <span data-ttu-id="a7eca-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7eca-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7eca-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7eca-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7eca-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7eca-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7eca-115">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7eca-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7eca-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7eca-116">See Also</span></span>  
 [<span data-ttu-id="a7eca-117">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7eca-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="a7eca-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a7eca-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
