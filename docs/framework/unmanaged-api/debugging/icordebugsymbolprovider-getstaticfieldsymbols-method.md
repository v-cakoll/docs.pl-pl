---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols — metoda
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7d5195215762c25b2d7dc2b71fcd53959656303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420898"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="0ca01-102">ICorDebugSymbolProvider::GetStaticFieldSymbols — metoda</span><span class="sxs-lookup"><span data-stu-id="0ca01-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="0ca01-103">Pobiera symbole statycznego pola, które odpowiadają podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="0ca01-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ca01-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ca01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ca01-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="0ca01-106">[in] Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0ca01-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="0ca01-107">[in] Tablica bajtów, który zawiera `typespec` podpisu.</span><span class="sxs-lookup"><span data-stu-id="0ca01-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="0ca01-108">[in] Liczba symbole żądanie.</span><span class="sxs-lookup"><span data-stu-id="0ca01-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="0ca01-109">[out] Wskaźnik do liczbę symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="0ca01-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="0ca01-110">[out] Wskaźnik do [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) tablica, która zawiera symbole żądanego pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="0ca01-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ca01-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ca01-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ca01-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0ca01-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca01-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ca01-113">Requirements</span></span>  
 <span data-ttu-id="0ca01-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ca01-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca01-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ca01-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ca01-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ca01-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ca01-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca01-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca01-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ca01-118">See Also</span></span>  
 [<span data-ttu-id="0ca01-119">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="0ca01-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)  
 [<span data-ttu-id="0ca01-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="0ca01-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="0ca01-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0ca01-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
