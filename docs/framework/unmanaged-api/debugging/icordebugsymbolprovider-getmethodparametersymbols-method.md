---
title: Metoda ICorDebugSymbolProvider::GetMethodParameterSymbols
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be103b8f9d6f94d5b7a265ec2ef01c551622c9e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714298"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a><span data-ttu-id="996a6-102">Metoda ICorDebugSymbolProvider::GetMethodParameterSymbols</span><span class="sxs-lookup"><span data-stu-id="996a6-102">ICorDebugSymbolProvider::GetMethodParameterSymbols Method</span></span>
<span data-ttu-id="996a6-103">Pobiera symbole parametru metody podany wirtualny adres względny (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="996a6-103">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="996a6-104">Syntax</span></span>  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="996a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="996a6-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="996a6-106">[in] Natywne wirtualny adres względny metody.</span><span class="sxs-lookup"><span data-stu-id="996a6-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="996a6-107">[in] Liczba symbole lokalne żądanie.</span><span class="sxs-lookup"><span data-stu-id="996a6-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="996a6-108">[out] Wskaźnik do liczby symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="996a6-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="996a6-109">[out] Wskaźnik do [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) tablicę, która zawiera symbole lokalne metody.</span><span class="sxs-lookup"><span data-stu-id="996a6-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="996a6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="996a6-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="996a6-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="996a6-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996a6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="996a6-112">Requirements</span></span>  
 <span data-ttu-id="996a6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996a6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996a6-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="996a6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="996a6-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="996a6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="996a6-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996a6-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996a6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="996a6-117">See also</span></span>
- [<span data-ttu-id="996a6-118">GetMethodLocalSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="996a6-118">GetMethodLocalSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [<span data-ttu-id="996a6-119">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="996a6-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="996a6-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="996a6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
