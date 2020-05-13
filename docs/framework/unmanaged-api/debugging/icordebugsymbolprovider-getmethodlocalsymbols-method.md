---
title: 'ICorDebugSymbolProvider:: GetMethodLocalSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 7e9aa01a3fa1c90b0ab4f85970c4eb294b9a4904
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379610"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a><span data-ttu-id="8147f-102">ICorDebugSymbolProvider:: GetMethodLocalSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="8147f-102">ICorDebugSymbolProvider::GetMethodLocalSymbols Method</span></span>
<span data-ttu-id="8147f-103">Pobiera symbole lokalne metody z uwzględnieniem względnego adresu wirtualnego (RVA) tej metody.</span><span class="sxs-lookup"><span data-stu-id="8147f-103">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8147f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8147f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8147f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8147f-105">Parameters</span></span>  
 `nativeRVA`  
 <span data-ttu-id="8147f-106">podczas Natywny względny adres wirtualny metody.</span><span class="sxs-lookup"><span data-stu-id="8147f-106">[in] The native relative virtual address of the method.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="8147f-107">podczas Liczba żądanych symboli lokalnych.</span><span class="sxs-lookup"><span data-stu-id="8147f-107">[in] The number of local symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="8147f-108">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="8147f-108">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="8147f-109">określoną Wskaźnik do tablicy [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) zawierającej symbole lokalne metody.</span><span class="sxs-lookup"><span data-stu-id="8147f-109">[out] A pointer to an [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) array that contains the method's local symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8147f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8147f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8147f-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8147f-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8147f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8147f-112">Requirements</span></span>  
 <span data-ttu-id="8147f-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8147f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8147f-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8147f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8147f-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8147f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8147f-116">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8147f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8147f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8147f-117">See also</span></span>

- [<span data-ttu-id="8147f-118">GetMethodParameterSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="8147f-118">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [<span data-ttu-id="8147f-119">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="8147f-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8147f-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8147f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
