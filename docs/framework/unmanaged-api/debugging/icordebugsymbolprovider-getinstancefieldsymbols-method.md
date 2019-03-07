---
title: ICorDebugSymbolProvider::GetInstanceFieldSymbols Method
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d149eeec545909d9d6b7413c7ad6d537c1493bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501321"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="9dd3d-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span><span class="sxs-lookup"><span data-stu-id="9dd3d-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="9dd3d-103">Pobiera wystąpienie symboli pola, które odpowiadają podpisu elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9dd3d-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dd3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dd3d-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="9dd3d-106">[in] Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="9dd3d-107">[in] Tablica bajtów, która zawiera `typespec` podpisu.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="9dd3d-108">[in] Liczba symboli żądanie.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="9dd3d-109">[out] Wskaźnik do liczby symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="9dd3d-110">[out] Wskaźnik do [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) tablicy, który zawiera symbole pola żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dd3d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9dd3d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9dd3d-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9dd3d-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dd3d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9dd3d-113">Requirements</span></span>  
 <span data-ttu-id="9dd3d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dd3d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd3d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dd3d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dd3d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dd3d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dd3d-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dd3d-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd3d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9dd3d-118">See also</span></span>
- [<span data-ttu-id="9dd3d-119">GetStaticFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="9dd3d-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="9dd3d-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="9dd3d-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9dd3d-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9dd3d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
