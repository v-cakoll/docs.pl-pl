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
ms.openlocfilehash: d2ddb0b9e10314d027d342b34542129fbcdfb075
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="09434-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols — metoda</span><span class="sxs-lookup"><span data-stu-id="09434-102">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>
<span data-ttu-id="09434-103">Pobiera wystąpienie symboli pola, które odpowiadają podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="09434-103">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09434-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09434-104">Syntax</span></span>  
  
```  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09434-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09434-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="09434-106">[in] Liczba bajtów w `typeSig` tablicy.</span><span class="sxs-lookup"><span data-stu-id="09434-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="09434-107">[in] Tablica bajtów, który zawiera `typespec` podpisu.</span><span class="sxs-lookup"><span data-stu-id="09434-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="09434-108">[in] Liczba symbole żądanie.</span><span class="sxs-lookup"><span data-stu-id="09434-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="09434-109">[out] Wskaźnik do liczbę symboli pobierane przez metodę.</span><span class="sxs-lookup"><span data-stu-id="09434-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="09434-110">[out] Wskaźnik do [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) tablica, która zawiera symbole pola żądanego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="09434-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09434-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09434-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09434-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09434-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09434-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09434-113">Requirements</span></span>  
 <span data-ttu-id="09434-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09434-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09434-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09434-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09434-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09434-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09434-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09434-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09434-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09434-118">See Also</span></span>  
 [<span data-ttu-id="09434-119">GetStaticFieldSymbols — metoda</span><span class="sxs-lookup"><span data-stu-id="09434-119">GetStaticFieldSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getstaticfieldsymbols-method.md)  
 [<span data-ttu-id="09434-120">Interfejs ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="09434-120">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="09434-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="09434-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
