---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols — metoda
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c590944c321050c9ecca330a2961a2a7b7f31e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="b35d3-102">ICorDebugSymbolProvider::GetMethodLocalSymbols — metoda</span><span class="sxs-lookup"><span data-stu-id="b35d3-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="b35d3-103">Pobiera symbole lokalne metody podany wirtualny adres względny (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="b35d3-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b35d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b35d3-104">Syntax</span></span>  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b35d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b35d3-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="b35d3-106">[in] Natywny wirtualny adres względny metody.</span><span class="sxs-lookup"><span data-stu-id="b35d3-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="b35d3-107">[in] Liczba symbole lokalne żądanie.</span><span class="sxs-lookup"><span data-stu-id="b35d3-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="b35d3-108">[out] Wskaźnik do liczbę symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="b35d3-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="b35d3-109">[out] Wskaźnik do [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tablica, która zawiera symbole lokalne metody.</span><span class="sxs-lookup"><span data-stu-id="b35d3-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b35d3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b35d3-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b35d3-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b35d3-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b35d3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b35d3-112">Requirements</span></span>  
 <span data-ttu-id="b35d3-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b35d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b35d3-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b35d3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b35d3-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b35d3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b35d3-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b35d3-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35d3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b35d3-117">See Also</span></span>  
 [<span data-ttu-id="b35d3-118">GetMethodParameterSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="b35d3-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)  
 [<span data-ttu-id="b35d3-119">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="b35d3-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="b35d3-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b35d3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
