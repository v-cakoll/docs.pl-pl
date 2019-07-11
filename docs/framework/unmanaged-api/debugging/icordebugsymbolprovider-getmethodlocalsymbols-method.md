---
title: ICorDebugSymbolProvider::GetMethodLocalSymbols Method
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac40123eff4028c1ebda898db27a5bd746571ba7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771403"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="2ece4-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span><span class="sxs-lookup"><span data-stu-id="2ece4-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="2ece4-103">Pobiera symbole lokalne metody podany wirtualny adres względny (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="2ece4-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ece4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ece4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ece4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ece4-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="2ece4-106">[in] Natywne wirtualny adres względny metody.</span><span class="sxs-lookup"><span data-stu-id="2ece4-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="2ece4-107">[in] Liczba symbole lokalne żądanie.</span><span class="sxs-lookup"><span data-stu-id="2ece4-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2ece4-108">[out] Wskaźnik do liczby symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="2ece4-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2ece4-109">[out] Wskaźnik do [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tablicę, która zawiera symbole lokalne metody.</span><span class="sxs-lookup"><span data-stu-id="2ece4-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ece4-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ece4-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ece4-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2ece4-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ece4-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2ece4-112">Requirements</span></span>  
 <span data-ttu-id="2ece4-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ece4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ece4-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ece4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ece4-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ece4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ece4-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ece4-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ece4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ece4-117">See also</span></span>

- [<span data-ttu-id="2ece4-118">GetMethodParameterSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="2ece4-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="2ece4-119">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="2ece4-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2ece4-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2ece4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
