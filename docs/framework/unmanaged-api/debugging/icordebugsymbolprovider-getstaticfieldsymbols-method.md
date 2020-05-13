---
title: 'ICorDebugSymbolProvider:: GetStaticFieldSymbols, Metoda'
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 2428521b9b08060fd147a7c9b9054239bf957f69
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379374"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="8f487-102">ICorDebugSymbolProvider:: GetStaticFieldSymbols, Metoda</span><span class="sxs-lookup"><span data-stu-id="8f487-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>
<span data-ttu-id="8f487-103">Pobiera symbole pól statycznych, które odpowiadają sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="8f487-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f487-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f487-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f487-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f487-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="8f487-106">podczas Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8f487-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="8f487-107">podczas Tablica bajtów, która zawiera `typespec` sygnaturę.</span><span class="sxs-lookup"><span data-stu-id="8f487-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="8f487-108">podczas Żądana liczba symboli.</span><span class="sxs-lookup"><span data-stu-id="8f487-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="8f487-109">określoną Wskaźnik do liczby symboli pobranych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="8f487-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="8f487-110">określoną Wskaźnik do tablicy [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) , która zawiera żądane symbole pól statycznych.</span><span class="sxs-lookup"><span data-stu-id="8f487-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f487-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f487-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f487-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8f487-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f487-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f487-113">Requirements</span></span>  
 <span data-ttu-id="8f487-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f487-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f487-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f487-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f487-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f487-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f487-117">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f487-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f487-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8f487-118">See also</span></span>

- [<span data-ttu-id="8f487-119">GetInstanceFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="8f487-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="8f487-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f487-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="8f487-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8f487-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
