---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd3442adf58250a423438666ec1092bab61958b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955534"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="88461-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="88461-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="88461-103">Pobiera symbole pól statycznych, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="88461-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88461-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88461-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88461-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="88461-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="88461-106">podczas Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="88461-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="88461-107">podczas Tablica bajtów, która zawiera `typespec` sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="88461-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="88461-108">podczas Żądana liczba symboli.</span><span class="sxs-lookup"><span data-stu-id="88461-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="88461-109">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="88461-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="88461-110">określoną Wskaźnik do tablicy [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) , która zawiera żądane symbole pól statycznych.</span><span class="sxs-lookup"><span data-stu-id="88461-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88461-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88461-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88461-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="88461-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88461-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88461-113">Requirements</span></span>  
 <span data-ttu-id="88461-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88461-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88461-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88461-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88461-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88461-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88461-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88461-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88461-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88461-118">See also</span></span>

- [<span data-ttu-id="88461-119">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="88461-119">GetInstanceFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="88461-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="88461-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="88461-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="88461-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
