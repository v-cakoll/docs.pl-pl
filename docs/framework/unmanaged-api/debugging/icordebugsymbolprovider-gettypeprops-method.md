---
title: "ICorDebugSymbolProvider::GetTypeProps — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba736caf8d8d823a4cb56c75aa2202ad616983fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="ee967-102">ICorDebugSymbolProvider::GetTypeProps — metoda</span><span class="sxs-lookup"><span data-stu-id="ee967-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="ee967-103">Zwraca informacje dotyczące typu właściwości, takie jak liczba podpisu jego parametry ogólne, podany wirtualny adres względny (RVA) w vtable.</span><span class="sxs-lookup"><span data-stu-id="ee967-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee967-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee967-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee967-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee967-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="ee967-106">[in] Wirtualny adres względny (RVA) w vtable.</span><span class="sxs-lookup"><span data-stu-id="ee967-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="ee967-107">[in] Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ee967-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="ee967-108">W sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="ee967-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="ee967-109">[out] [out] Wskaźnik do rozmiaru zwracana `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ee967-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="ee967-110">[out] Buforu, który zawiera podpisy elementu typespec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="ee967-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee967-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee967-111">Remarks</span></span>  
 <span data-ttu-id="ee967-112">Aby uzyskać wymagany rozmiar typu `signature` tablicy, ustaw `cbSignature` argument 0 i `signature` do **null**.</span><span class="sxs-lookup"><span data-stu-id="ee967-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="ee967-113">Gdy metoda zwróci wartość, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ee967-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee967-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ee967-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee967-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee967-115">Requirements</span></span>  
 <span data-ttu-id="ee967-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee967-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee967-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee967-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee967-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee967-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee967-119">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee967-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee967-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee967-120">See Also</span></span>  
 [<span data-ttu-id="ee967-121">GetMethodProps — metoda</span><span class="sxs-lookup"><span data-stu-id="ee967-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)  
 [<span data-ttu-id="ee967-122">Interfejs ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="ee967-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="ee967-123">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="ee967-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
