---
title: ICorDebugSymbolProvider::GetObjectSize — metoda
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da526ac133604fa43081f86988459c4238517c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421506"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="0c40f-102">ICorDebugSymbolProvider::GetObjectSize — metoda</span><span class="sxs-lookup"><span data-stu-id="0c40f-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="0c40f-103">Zwraca rozmiar obiektu dla obiektu, w oparciu o jego sygnatura elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="0c40f-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c40f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c40f-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c40f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c40f-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="0c40f-106">[in] Liczba bajtów w podpisie elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="0c40f-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="0c40f-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="0c40f-107">typeSig</span></span>  
 <span data-ttu-id="0c40f-108">[in] Podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="0c40f-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="0c40f-109">[out] Wskaźnik do rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="0c40f-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c40f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c40f-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c40f-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0c40f-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c40f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c40f-112">Requirements</span></span>  
 <span data-ttu-id="0c40f-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c40f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c40f-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c40f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c40f-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c40f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c40f-116">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c40f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c40f-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c40f-117">See Also</span></span>  
 [<span data-ttu-id="0c40f-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c40f-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="0c40f-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0c40f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
