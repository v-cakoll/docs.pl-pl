---
title: 'ICorDebugSymbolProvider:: GetObjectSize —, Metoda'
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59054d7b939ab29cb08c30961601a323529ce06b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955629"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="30deb-102">ICorDebugSymbolProvider:: GetObjectSize —, Metoda</span><span class="sxs-lookup"><span data-stu-id="30deb-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>
<span data-ttu-id="30deb-103">Zwraca rozmiar obiektu na podstawie jego podpisu elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="30deb-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30deb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="30deb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30deb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="30deb-105">Parameters</span></span>  
 `cbSignature`  
 <span data-ttu-id="30deb-106">podczas Liczba bajtów w sygnaturze elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="30deb-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="30deb-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="30deb-107">typeSig</span></span>  
 <span data-ttu-id="30deb-108">podczas Sygnatura elementu TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="30deb-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="30deb-109">określoną Wskaźnik do rozmiaru obiektu.</span><span class="sxs-lookup"><span data-stu-id="30deb-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30deb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="30deb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30deb-111">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="30deb-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30deb-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="30deb-112">Requirements</span></span>  
 <span data-ttu-id="30deb-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30deb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30deb-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30deb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30deb-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30deb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30deb-116">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30deb-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30deb-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30deb-117">See also</span></span>

- [<span data-ttu-id="30deb-118">ICorDebugSymbolProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="30deb-118">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="30deb-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="30deb-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
