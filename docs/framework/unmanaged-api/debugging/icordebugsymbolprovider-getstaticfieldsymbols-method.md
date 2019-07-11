---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols Method
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9379a335130242918f6fe200eeda5e4c262fd020
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771312"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="1d4c8-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span><span class="sxs-lookup"><span data-stu-id="1d4c8-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="1d4c8-103">Pobiera symbole pole statyczne, które odpowiadają podpisu elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d4c8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d4c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d4c8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d4c8-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="1d4c8-106">[in] Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="1d4c8-107">[in] Tablica bajtów, która zawiera `typespec` podpisu.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="1d4c8-108">[in] Liczba symboli żądanie.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="1d4c8-109">[out] Wskaźnik do liczby symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="1d4c8-110">[out] Wskaźnik do [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) tablicy, który zawiera symbole żądane pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d4c8-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d4c8-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d4c8-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1d4c8-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d4c8-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d4c8-113">Requirements</span></span>  
 <span data-ttu-id="1d4c8-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d4c8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d4c8-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1d4c8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1d4c8-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1d4c8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1d4c8-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d4c8-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4c8-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d4c8-118">See also</span></span>

- [<span data-ttu-id="1d4c8-119">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="1d4c8-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="1d4c8-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d4c8-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1d4c8-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1d4c8-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
