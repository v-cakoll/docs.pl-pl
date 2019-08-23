---
title: 'ICorDebugSymbolProvider:: GetMethodProps —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95610bc527b8f5b90df906b6260eb636d61dbcd8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957306"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="dc720-102">ICorDebugSymbolProvider:: GetMethodProps —, Metoda</span><span class="sxs-lookup"><span data-stu-id="dc720-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="dc720-103">Zwraca informacje o właściwościach metody, takich jak token metadanych metody i informacje o jego ogólnych parametrach, w którym znajduje się względny adres wirtualny (RVA) w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="dc720-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc720-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc720-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="dc720-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc720-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="dc720-106">podczas Względny adres wirtualny w metodzie, o które informacje mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="dc720-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="dc720-107">określoną Wskaźnik do tokenu metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="dc720-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="dc720-108">określoną Wskaźnik do liczby parametrów ogólnych skojarzonych z tą metodą.</span><span class="sxs-lookup"><span data-stu-id="dc720-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="dc720-109">podczas Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="dc720-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="dc720-110">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="dc720-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="dc720-111">określoną Wskaźnik do rozmiaru zwróconej `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="dc720-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="dc720-112">określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="dc720-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc720-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc720-113">Remarks</span></span>  
 <span data-ttu-id="dc720-114">Aby uzyskać wymagany `signature` rozmiar tablicy metody, należy `cbSignature` ustawić argument na 0 i `signature` na **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="dc720-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="dc720-115">Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganych `signature` przez tablicę.</span><span class="sxs-lookup"><span data-stu-id="dc720-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc720-116">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dc720-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc720-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc720-117">Requirements</span></span>  
 <span data-ttu-id="dc720-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc720-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc720-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dc720-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dc720-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc720-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc720-121">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc720-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc720-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc720-122">See also</span></span>

- [<span data-ttu-id="dc720-123">GetTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="dc720-123">GetTypeProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="dc720-124">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="dc720-124">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dc720-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="dc720-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
