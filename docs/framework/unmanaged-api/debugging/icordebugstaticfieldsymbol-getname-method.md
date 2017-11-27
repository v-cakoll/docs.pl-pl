---
title: "ICorDebugStaticFieldSymbol::GetName — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: af3cea14e29c987d2d24d5adc803afd5b9084651
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="2c9e6-102">ICorDebugStaticFieldSymbol::GetName — metoda</span><span class="sxs-lookup"><span data-stu-id="2c9e6-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="2c9e6-103">Pobiera nazwę pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="2c9e6-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9e6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c9e6-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c9e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c9e6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2c9e6-106">[in] Liczba znaków w `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="2c9e6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2c9e6-107">[out] Wskaźnik do liczby znaków faktycznie zapisane `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="2c9e6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="2c9e6-108">[out] Tablica znaków, która przechowuje nazwę zwrócony.</span><span class="sxs-lookup"><span data-stu-id="2c9e6-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c9e6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c9e6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c9e6-110">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2c9e6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c9e6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c9e6-111">Requirements</span></span>  
 <span data-ttu-id="2c9e6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c9e6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c9e6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c9e6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c9e6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c9e6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c9e6-115">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c9e6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9e6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c9e6-116">See Also</span></span>  
 [<span data-ttu-id="2c9e6-117">Interfejs ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="2c9e6-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="2c9e6-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="2c9e6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
