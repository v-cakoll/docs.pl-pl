---
title: "ICorDebugSymbolProvider::GetObjectSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8817eb79c825a02ec5654ec340dedd6c77889a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="bf681-102">ICorDebugSymbolProvider::GetObjectSize — metoda</span><span class="sxs-lookup"><span data-stu-id="bf681-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="bf681-103">Zwraca rozmiar obiektu dla obiektu, w oparciu o jego sygnatura elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="bf681-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf681-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf681-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf681-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf681-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="bf681-106">[in] Liczba bajtów w podpisie elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="bf681-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="bf681-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="bf681-107">typeSig</span></span>  
 <span data-ttu-id="bf681-108">[in] Podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="bf681-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="bf681-109">[out] Wskaźnik do rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="bf681-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf681-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf681-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf681-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bf681-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf681-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf681-112">Requirements</span></span>  
 <span data-ttu-id="bf681-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf681-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf681-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf681-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf681-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf681-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf681-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf681-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf681-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf681-117">See Also</span></span>  
 [<span data-ttu-id="bf681-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="bf681-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="bf681-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bf681-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
