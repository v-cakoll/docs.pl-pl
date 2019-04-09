---
title: ICorDebugSymbolProvider::GetTypeProps Method
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5f9867dbdc244ed22948dbe9a07a7ea06292d6a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079087"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="e5c8a-102">ICorDebugSymbolProvider::GetTypeProps Method</span><span class="sxs-lookup"><span data-stu-id="e5c8a-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="e5c8a-103">Zwraca informacje o właściwościach typu, takie jak liczba podpisu parametrami rodzajowymi, rozpoczynając od podanej względnych adresów wirtualnych (RVA) w vtable.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5c8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5c8a-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5c8a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e5c8a-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="e5c8a-106">[in] Względny adres wirtualny (RVA) w vtable.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="e5c8a-107">[in] Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="e5c8a-108">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="e5c8a-109">[out] [out] Wskaźnik do rozmiaru zwracanego `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="e5c8a-110">[out] Buforu, który zawiera sygnatury elementu typespec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5c8a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5c8a-111">Remarks</span></span>  
 <span data-ttu-id="e5c8a-112">Aby uzyskać wymagany rozmiar typu `signature` tablicy, należy ustawić `cbSignature` argument 0 i `signature` do **o wartości null**.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="e5c8a-113">Po powrocie z metody `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c8a-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e5c8a-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5c8a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5c8a-115">Requirements</span></span>  
 <span data-ttu-id="e5c8a-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5c8a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5c8a-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5c8a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5c8a-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5c8a-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e5c8a-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e5c8a-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5c8a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e5c8a-120">See also</span></span>

- [<span data-ttu-id="e5c8a-121">GetMethodProps, metoda</span><span class="sxs-lookup"><span data-stu-id="e5c8a-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="e5c8a-122">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="e5c8a-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e5c8a-123">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="e5c8a-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
