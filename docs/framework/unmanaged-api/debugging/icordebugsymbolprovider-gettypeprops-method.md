---
title: ICorDebugSymbolProvider::GetTypeProps Method
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e21273506e91c5ab69b1b0b4a52d6c0f72692dab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712775"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="7ee1c-102">ICorDebugSymbolProvider::GetTypeProps Method</span><span class="sxs-lookup"><span data-stu-id="7ee1c-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="7ee1c-103">Zwraca informacje o właściwościach typu, takie jak liczba podpisu parametrami rodzajowymi, rozpoczynając od podanej względnych adresów wirtualnych (RVA) w vtable.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ee1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7ee1c-104">Syntax</span></span>  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ee1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ee1c-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="7ee1c-106">[in] Względny adres wirtualny (RVA) w vtable.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="7ee1c-107">[in] Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="7ee1c-108">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="7ee1c-109">[out] [out] Wskaźnik do rozmiaru zwracanego `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="7ee1c-110">[out] Buforu, który zawiera sygnatury elementu typespec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ee1c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ee1c-111">Remarks</span></span>  
 <span data-ttu-id="7ee1c-112">Aby uzyskać wymagany rozmiar typu `signature` tablicy, należy ustawić `cbSignature` argument 0 i `signature` do **o wartości null**.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="7ee1c-113">Po powrocie z metody `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ee1c-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7ee1c-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ee1c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ee1c-115">Requirements</span></span>  
 <span data-ttu-id="7ee1c-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ee1c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ee1c-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ee1c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ee1c-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ee1c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ee1c-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ee1c-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ee1c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ee1c-120">See also</span></span>
- [<span data-ttu-id="7ee1c-121">GetMethodProps, metoda</span><span class="sxs-lookup"><span data-stu-id="7ee1c-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="7ee1c-122">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="7ee1c-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="7ee1c-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7ee1c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
