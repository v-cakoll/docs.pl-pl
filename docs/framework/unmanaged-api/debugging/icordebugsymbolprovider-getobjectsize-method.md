---
title: ICorDebugSymbolProvider::GetObjectSize Method
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcdb5541fdd49944f462321dc24131a32a42391
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107292"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="612a8-102">ICorDebugSymbolProvider::GetObjectSize Method</span><span class="sxs-lookup"><span data-stu-id="612a8-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="612a8-103">Zwraca rozmiar obiektu dla obiektu, w oparciu o jego podpisu elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="612a8-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="612a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="612a8-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="612a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="612a8-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="612a8-106">[in] Liczba bajtów w podpisie elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="612a8-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="612a8-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="612a8-107">typeSig</span></span>  
 <span data-ttu-id="612a8-108">[in] Podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="612a8-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="612a8-109">[out] Wskaźnik do rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="612a8-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="612a8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="612a8-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="612a8-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="612a8-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="612a8-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="612a8-112">Requirements</span></span>  
 <span data-ttu-id="612a8-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="612a8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="612a8-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="612a8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="612a8-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="612a8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="612a8-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="612a8-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="612a8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="612a8-117">See also</span></span>

- [<span data-ttu-id="612a8-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="612a8-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="612a8-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="612a8-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
