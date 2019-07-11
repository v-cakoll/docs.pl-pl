---
title: ICorDebugSymbolProvider::GetObjectSize Method
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b90e2a097e6dfd35b6237808a7b8b47937774b0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771318"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="45bb5-102">ICorDebugSymbolProvider::GetObjectSize Method</span><span class="sxs-lookup"><span data-stu-id="45bb5-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="45bb5-103">Zwraca rozmiar obiektu dla obiektu, w oparciu o jego podpisu elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="45bb5-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45bb5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45bb5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45bb5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45bb5-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="45bb5-106">[in] Liczba bajtów w podpisie elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="45bb5-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="45bb5-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="45bb5-107">typeSig</span></span>  
 <span data-ttu-id="45bb5-108">[in] Podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="45bb5-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="45bb5-109">[out] Wskaźnik do rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="45bb5-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45bb5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45bb5-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45bb5-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="45bb5-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45bb5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45bb5-112">Requirements</span></span>  
 <span data-ttu-id="45bb5-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45bb5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45bb5-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45bb5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45bb5-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45bb5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45bb5-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45bb5-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45bb5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45bb5-117">See also</span></span>

- [<span data-ttu-id="45bb5-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="45bb5-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="45bb5-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="45bb5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
