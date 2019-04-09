---
title: ICorDebugSymbolProvider::GetObjectSize Method
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcdb5541fdd49944f462321dc24131a32a42391
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107292"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="c34b1-102">ICorDebugSymbolProvider::GetObjectSize Method</span><span class="sxs-lookup"><span data-stu-id="c34b1-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="c34b1-103">Zwraca rozmiar obiektu dla obiektu, w oparciu o jego podpisu elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="c34b1-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c34b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c34b1-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c34b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c34b1-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="c34b1-106">[in] Liczba bajtów w podpisie elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="c34b1-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="c34b1-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="c34b1-107">typeSig</span></span>  
 <span data-ttu-id="c34b1-108">[in] Podpis elementu typespec.</span><span class="sxs-lookup"><span data-stu-id="c34b1-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="c34b1-109">[out] Wskaźnik do rozmiar obiektu.</span><span class="sxs-lookup"><span data-stu-id="c34b1-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c34b1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c34b1-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c34b1-111">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c34b1-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c34b1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c34b1-112">Requirements</span></span>  
 <span data-ttu-id="c34b1-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c34b1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c34b1-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c34b1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c34b1-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c34b1-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c34b1-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c34b1-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c34b1-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c34b1-117">See also</span></span>

- [<span data-ttu-id="c34b1-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="c34b1-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="c34b1-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c34b1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
