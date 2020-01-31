---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 02cc62a421058f83e28ce945ae9e76745f768988
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791555"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="42b04-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="42b04-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="42b04-103">Pobiera symbole pól statycznych, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="42b04-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42b04-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42b04-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42b04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="42b04-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="42b04-106">podczas Liczba bajtów w tablicy `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="42b04-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="42b04-107">podczas Tablica bajtów, która zawiera sygnaturę `typespec`.</span><span class="sxs-lookup"><span data-stu-id="42b04-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="42b04-108">podczas Żądana liczba symboli.</span><span class="sxs-lookup"><span data-stu-id="42b04-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="42b04-109">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="42b04-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="42b04-110">określoną Wskaźnik do tablicy [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) , która zawiera żądane symbole pól statycznych.</span><span class="sxs-lookup"><span data-stu-id="42b04-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42b04-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42b04-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42b04-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="42b04-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42b04-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42b04-113">Requirements</span></span>  
 <span data-ttu-id="42b04-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42b04-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42b04-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="42b04-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42b04-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="42b04-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42b04-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42b04-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42b04-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42b04-118">See also</span></span>

- [<span data-ttu-id="42b04-119">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="42b04-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="42b04-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="42b04-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="42b04-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="42b04-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
