---
title: 'ICorDebugSymbolProvider:: GetTypeProps, Metoda'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: c87d9f6d0a719dae5e532e9c0369a7f9fc03748a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133669"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="df849-102">ICorDebugSymbolProvider:: GetTypeProps, Metoda</span><span class="sxs-lookup"><span data-stu-id="df849-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>
<span data-ttu-id="df849-103">Zwraca informacje o właściwościach typu, takich jak liczba podpisów jego parametrów ogólnych, z uwzględnieniem względnego adresu wirtualnego (RVA) w tabeli jednoelementowej.</span><span class="sxs-lookup"><span data-stu-id="df849-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df849-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df849-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df849-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df849-105">Parameters</span></span>  
 `tableRva`  
 <span data-ttu-id="df849-106">podczas Względny adres wirtualny (RVA) w tabeli jednoelementowej.</span><span class="sxs-lookup"><span data-stu-id="df849-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="df849-107">podczas Rozmiar tablicy `signature`.</span><span class="sxs-lookup"><span data-stu-id="df849-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="df849-108">Zobacz sekcję Uwagi.</span><span class="sxs-lookup"><span data-stu-id="df849-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="df849-109">określoną określoną Wskaźnik do rozmiaru zwróconej tablicy `signature`.</span><span class="sxs-lookup"><span data-stu-id="df849-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="df849-110">określoną Bufor, który przechowuje sygnatury elementu TypeSpec wszystkich parametrów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="df849-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df849-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df849-111">Remarks</span></span>  
 <span data-ttu-id="df849-112">Aby uzyskać wymagany rozmiar tablicy `signature` typu, ustaw dla argumentu `cbSignature` wartość 0, a `signature` na **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="df849-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="df849-113">Gdy metoda zwraca, `pcbSignature` będzie zawierać liczbę bajtów wymaganą dla `signature` tablicy.</span><span class="sxs-lookup"><span data-stu-id="df849-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="df849-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="df849-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df849-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df849-115">Requirements</span></span>  
 <span data-ttu-id="df849-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df849-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df849-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="df849-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df849-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="df849-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df849-119">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df849-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df849-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df849-120">See also</span></span>

- [<span data-ttu-id="df849-121">GetMethodProps, metoda</span><span class="sxs-lookup"><span data-stu-id="df849-121">GetMethodProps Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="df849-122">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="df849-122">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="df849-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="df849-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
