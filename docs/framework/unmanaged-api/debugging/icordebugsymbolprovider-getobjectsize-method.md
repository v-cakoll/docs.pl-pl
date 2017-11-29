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
ms.openlocfilehash: ea9e0fcae9f98869884ad887a6c24de342512b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="4db5d-102">ICorDebugSymbolProvider::GetObjectSize — metoda</span><span class="sxs-lookup"><span data-stu-id="4db5d-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="4db5d-103">Zwraca rozmiar obiektu dla obiektu, w oparciu o jego sygnatura elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="4db5d-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4db5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4db5d-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4db5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4db5d-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="4db5d-106">[in] Liczba bajtów w podpisie elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="4db5d-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="4db5d-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="4db5d-107">typeSig</span></span>  
 <span data-ttu-id="4db5d-108">[in] Podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="4db5d-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="4db5d-109">[out] Wskaźnik do rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="4db5d-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4db5d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4db5d-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4db5d-111">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4db5d-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4db5d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4db5d-112">Requirements</span></span>  
 <span data-ttu-id="4db5d-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4db5d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4db5d-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4db5d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4db5d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4db5d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4db5d-116">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4db5d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db5d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4db5d-117">See Also</span></span>  
 [<span data-ttu-id="4db5d-118">Interfejs ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="4db5d-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="4db5d-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="4db5d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
