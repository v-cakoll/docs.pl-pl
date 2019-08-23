---
title: 'ICorDebugStaticFieldSymbol:: GetAddress — Metoda'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d41b99d7410333cb6a22443271c1fcbc41c3594
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962699"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="d7b54-102">ICorDebugStaticFieldSymbol:: GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7b54-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="d7b54-103">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="d7b54-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7b54-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7b54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7b54-105">Parameters</span></span>  
 <span data-ttu-id="d7b54-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="d7b54-106">pRVA</span></span>  
 <span data-ttu-id="d7b54-107">określoną Wskaźnik do względnego adresu wirtualnego (RVA) pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="d7b54-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7b54-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7b54-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7b54-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d7b54-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7b54-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7b54-110">Requirements</span></span>  
 <span data-ttu-id="d7b54-111">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7b54-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7b54-112">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7b54-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7b54-113">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7b54-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7b54-114">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7b54-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7b54-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7b54-115">See also</span></span>

- [<span data-ttu-id="d7b54-116">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7b54-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="d7b54-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d7b54-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
