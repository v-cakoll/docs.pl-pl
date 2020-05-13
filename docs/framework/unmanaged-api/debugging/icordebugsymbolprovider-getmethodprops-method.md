---
title: 'ICorDebugSymbolProvider:: GetMethodProps —, Metoda'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: c9e73c4de7389405d9e4b643036709ff2dbb82e6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379562"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="ec195-102">ICorDebugSymbolProvider:: GetMethodProps —, Metoda</span><span class="sxs-lookup"><span data-stu-id="ec195-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>
<span data-ttu-id="ec195-103">Zwraca informacje o właściwościach metody, takich jak token metadanych metody i informacje o jego ogólnych parametrach, w którym znajduje się względny adres wirtualny (RVA) w tej metodzie.</span><span class="sxs-lookup"><span data-stu-id="ec195-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec195-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec195-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ec195-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec195-105">Parameters</span></span>  
 `codeRVA`  
 <span data-ttu-id="ec195-106">podczas Względny adres wirtualny w metodzie, o które informacje mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="ec195-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="ec195-107">określoną Wskaźnik do tokenu metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="ec195-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="ec195-108">określoną Wskaźnik do liczby parametrów ogólnych skojarzonych z tą metodą.</span><span class="sxs-lookup"><span data-stu-id="ec195-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="ec195-109">podczas Rozmiar `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ec195-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="ec195-110">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="ec195-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="ec195-111">określoną Wskaźnik do rozmiaru zwróconej `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="ec195-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="ec195-112">określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="ec195-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec195-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec195-113">Remarks</span></span>  
 <span data-ttu-id="ec195-114">Aby uzyskać wymagany rozmiar `signature` tablicy metody, należy ustawić `cbSignature` argument na 0 i `signature` na **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="ec195-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="ec195-115">Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganych przez `signature` tablicę.</span><span class="sxs-lookup"><span data-stu-id="ec195-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec195-116">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ec195-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec195-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec195-117">Requirements</span></span>  
 <span data-ttu-id="ec195-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec195-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec195-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec195-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec195-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec195-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec195-121">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec195-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec195-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec195-122">See also</span></span>

- [<span data-ttu-id="ec195-123">GetTypeProps, metoda</span><span class="sxs-lookup"><span data-stu-id="ec195-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="ec195-124">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec195-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ec195-125">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ec195-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
