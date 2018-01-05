---
title: "ICorDebugSymbolProvider::GetInstanceFieldSymbols — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6b40a3656abc6b6d882e7318d46f9dc189a4eb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="23b3a-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols — metoda</span><span class="sxs-lookup"><span data-stu-id="23b3a-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="23b3a-103">Pobiera wystąpienie symboli pola, które odpowiadają podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="23b3a-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23b3a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23b3a-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23b3a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23b3a-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="23b3a-106">[in] Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="23b3a-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="23b3a-107">[in] Tablica bajtów, który zawiera `typespec` podpisu.</span><span class="sxs-lookup"><span data-stu-id="23b3a-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="23b3a-108">[in] Liczba symbole żądanie.</span><span class="sxs-lookup"><span data-stu-id="23b3a-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="23b3a-109">[out] Wskaźnik do liczbę symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="23b3a-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="23b3a-110">[out] Wskaźnik do [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) tablica, która zawiera symbole pola żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="23b3a-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23b3a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23b3a-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23b3a-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="23b3a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23b3a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23b3a-113">Requirements</span></span>  
 <span data-ttu-id="23b3a-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23b3a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23b3a-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23b3a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23b3a-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23b3a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23b3a-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23b3a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b3a-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23b3a-118">See Also</span></span>  
 [<span data-ttu-id="23b3a-119">GetStaticFieldSymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="23b3a-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)  
 [<span data-ttu-id="23b3a-120">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="23b3a-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="23b3a-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="23b3a-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
