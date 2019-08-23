---
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24671c371ae8a0a9f3c7ca650a71298c69e2fae1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955671"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="2e74c-102">ICorDebugSymbolProvider:: GetMethodLocalSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="2e74c-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="2e74c-103">Pobiera symbole lokalne metody z uwzględnieniem względnego adresu wirtualnego (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="2e74c-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e74c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e74c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e74c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e74c-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="2e74c-106">podczas Natywny względny adres wirtualny metody.</span><span class="sxs-lookup"><span data-stu-id="2e74c-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="2e74c-107">podczas Liczba żądanych symboli lokalnych.</span><span class="sxs-lookup"><span data-stu-id="2e74c-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2e74c-108">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="2e74c-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="2e74c-109">określoną Wskaźnik do tablicy [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) zawierającej symbole lokalne metody.</span><span class="sxs-lookup"><span data-stu-id="2e74c-109">[out] A pointer to an [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e74c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e74c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e74c-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2e74c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e74c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e74c-112">Requirements</span></span>  
 <span data-ttu-id="2e74c-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e74c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e74c-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e74c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e74c-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e74c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e74c-116">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e74c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e74c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e74c-117">See also</span></span>

- [<span data-ttu-id="2e74c-118">GetMethodParameterSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="2e74c-118">GetMethodParameterSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="2e74c-119">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="2e74c-119">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="2e74c-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2e74c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
