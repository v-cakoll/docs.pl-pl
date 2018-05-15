---
title: ICorDebugSymbolProvider::GetMethodProps — metoda
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f52d20b9cb717d72d660bb19a0474c3e5b293ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="8038d-102">ICorDebugSymbolProvider::GetMethodProps — metoda</span><span class="sxs-lookup"><span data-stu-id="8038d-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="8038d-103">Zwraca informacje o właściwości metody, takie jak token metadanych oraz informacje o jego parametrów ogólnych — metoda podany wirtualny adres względny (RVA) w tej metody.</span><span class="sxs-lookup"><span data-stu-id="8038d-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8038d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8038d-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8038d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8038d-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="8038d-106">[in] Wirtualny adres względny w metodzie o tym, które ma być pobrana informacji.</span><span class="sxs-lookup"><span data-stu-id="8038d-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="8038d-107">[out] Wskaźnik do metody token metadanych.</span><span class="sxs-lookup"><span data-stu-id="8038d-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="8038d-108">[out] Wskaźnik do liczby parametrów ogólnych skojarzonych z tą metodą.</span><span class="sxs-lookup"><span data-stu-id="8038d-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="8038d-109">[in] Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8038d-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="8038d-110">W sekcji uwag.</span><span class="sxs-lookup"><span data-stu-id="8038d-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="8038d-111">[out] Wskaźnik do rozmiaru zwracana `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8038d-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="8038d-112">[out] Buforu, który zawiera podpisy elementu typespec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="8038d-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8038d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8038d-113">Remarks</span></span>  
 <span data-ttu-id="8038d-114">Aby uzyskać wymagany rozmiar metody `signature` tablicy, ustaw `cbSignature` argument 0 i `signature` do **null**.</span><span class="sxs-lookup"><span data-stu-id="8038d-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="8038d-115">Gdy metoda zwróci wartość, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="8038d-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8038d-116">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8038d-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8038d-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8038d-117">Requirements</span></span>  
 <span data-ttu-id="8038d-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8038d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8038d-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8038d-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8038d-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8038d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8038d-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8038d-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8038d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8038d-122">See Also</span></span>  
 [<span data-ttu-id="8038d-123">GetTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="8038d-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)  
 [<span data-ttu-id="8038d-124">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="8038d-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="8038d-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8038d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
