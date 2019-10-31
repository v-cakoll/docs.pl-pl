---
title: 'ICorDebugSymbolProvider:: GetObjectSize —, Metoda'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: a5c0fe6d73302abbfabe2272cc878d6fd8f5fdec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138816"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="b6d80-102">ICorDebugSymbolProvider:: GetObjectSize —, Metoda</span><span class="sxs-lookup"><span data-stu-id="b6d80-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="b6d80-103">Zwraca rozmiar obiektu na podstawie jego podpisu elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="b6d80-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6d80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6d80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6d80-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="b6d80-106">podczas Liczba bajtów w sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="b6d80-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="b6d80-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="b6d80-107">typeSig</span></span>  
 <span data-ttu-id="b6d80-108">podczas Sygnatura elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="b6d80-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="b6d80-109">określoną Wskaźnik do rozmiaru obiektu.</span><span class="sxs-lookup"><span data-stu-id="b6d80-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6d80-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6d80-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6d80-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b6d80-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6d80-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6d80-112">Requirements</span></span>  
 <span data-ttu-id="b6d80-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6d80-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6d80-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6d80-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6d80-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6d80-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6d80-116">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6d80-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6d80-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6d80-117">See also</span></span>

- [<span data-ttu-id="b6d80-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6d80-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="b6d80-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6d80-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
