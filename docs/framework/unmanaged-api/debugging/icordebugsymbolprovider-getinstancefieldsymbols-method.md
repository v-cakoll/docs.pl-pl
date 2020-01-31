---
title: 'ICorDebugSymbolProvider:: GetInstanceFieldSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 9c55ce4d36681e173047cfb51515a74899c5a9fe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791631"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="ff682-102">ICorDebugSymbolProvider:: GetInstanceFieldSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="ff682-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="ff682-103">Pobiera symbole pól wystąpienia, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="ff682-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff682-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff682-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff682-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff682-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="ff682-106">podczas Liczba bajtów w tablicy `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="ff682-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="ff682-107">podczas Tablica bajtów, która zawiera sygnaturę `typespec`.</span><span class="sxs-lookup"><span data-stu-id="ff682-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="ff682-108">podczas Żądana liczba symboli.</span><span class="sxs-lookup"><span data-stu-id="ff682-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="ff682-109">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="ff682-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="ff682-110">określoną Wskaźnik do tablicy [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) , która zawiera żądane symbole pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ff682-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff682-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff682-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff682-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ff682-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff682-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff682-113">Requirements</span></span>  
 <span data-ttu-id="ff682-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff682-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff682-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff682-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff682-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff682-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff682-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff682-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff682-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff682-118">See also</span></span>

- [<span data-ttu-id="ff682-119">GetStaticFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="ff682-119">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="ff682-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="ff682-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ff682-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ff682-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
