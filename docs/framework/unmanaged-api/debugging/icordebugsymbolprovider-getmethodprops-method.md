---
title: Metoda ICorDebugSymbolProvider::GetMethodProps
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f6971c7991f5e54973d96d9b3f662b54be564d9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771330"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="05b89-102">Metoda ICorDebugSymbolProvider::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="05b89-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="05b89-103">Zwraca informacje o właściwości metody, takie jak metody token metadanych oraz informacje o jego parametrów ogólnych, biorąc pod uwagę względnych adresów wirtualnych (RVA) w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="05b89-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b89-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05b89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05b89-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05b89-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="05b89-106">[in] Względny adres wirtualny w metodzie o tym, jakie informacje są do pobrania.</span><span class="sxs-lookup"><span data-stu-id="05b89-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="05b89-107">[out] Wskaźnik do metody token metadanych.</span><span class="sxs-lookup"><span data-stu-id="05b89-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="05b89-108">[out] Wskaźnik do liczby parametrów ogólnych skojarzone z tą metodą.</span><span class="sxs-lookup"><span data-stu-id="05b89-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="05b89-109">[in] Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="05b89-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="05b89-110">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="05b89-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="05b89-111">[out] Wskaźnik do rozmiaru zwracanego `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="05b89-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="05b89-112">[out] Buforu, który zawiera sygnatury elementu typespec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="05b89-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05b89-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05b89-113">Remarks</span></span>  
 <span data-ttu-id="05b89-114">Aby uzyskać wymagany rozmiar metody `signature` tablicy, należy ustawić `cbSignature` argument 0 i `signature` do **null**.</span><span class="sxs-lookup"><span data-stu-id="05b89-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="05b89-115">Po powrocie z metody `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="05b89-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="05b89-116">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="05b89-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b89-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05b89-117">Requirements</span></span>  
 <span data-ttu-id="05b89-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05b89-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b89-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05b89-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05b89-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b89-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b89-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b89-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b89-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05b89-122">See also</span></span>

- [<span data-ttu-id="05b89-123">GetTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="05b89-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="05b89-124">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="05b89-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="05b89-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="05b89-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
