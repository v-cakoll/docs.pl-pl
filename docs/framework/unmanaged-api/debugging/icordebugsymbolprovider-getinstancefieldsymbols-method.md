---
title: 'ICorDebugSymbolProvider:: GetInstanceFieldSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 0ad8ddd78d963681c0b2f69bf0f211ad464dc7b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138881"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="0f323-102">ICorDebugSymbolProvider:: GetInstanceFieldSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="0f323-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="0f323-103">Pobiera symbole pól wystąpienia, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="0f323-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f323-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f323-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f323-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f323-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="0f323-106">podczas Liczba bajtów w tablicy `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="0f323-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="0f323-107">podczas Tablica bajtów, która zawiera sygnaturę `typespec`.</span><span class="sxs-lookup"><span data-stu-id="0f323-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="0f323-108">podczas Żądana liczba symboli.</span><span class="sxs-lookup"><span data-stu-id="0f323-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="0f323-109">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="0f323-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="0f323-110">określoną Wskaźnik do tablicy [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) , która zawiera żądane symbole pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0f323-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f323-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f323-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f323-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0f323-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f323-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f323-113">Requirements</span></span>  
 <span data-ttu-id="0f323-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f323-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f323-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0f323-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0f323-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0f323-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f323-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f323-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f323-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f323-118">See also</span></span>

- [<span data-ttu-id="0f323-119">GetStaticFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="0f323-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="0f323-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f323-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="0f323-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0f323-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
