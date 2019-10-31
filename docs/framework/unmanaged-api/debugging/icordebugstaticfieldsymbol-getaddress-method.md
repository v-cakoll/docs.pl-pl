---
title: 'ICorDebugStaticFieldSymbol:: GetAddress — Metoda'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 65761e48491b2a4c81ccd05b17d8723f71f52e5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131798"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="e63b6-102">ICorDebugStaticFieldSymbol:: GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="e63b6-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="e63b6-103">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="e63b6-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e63b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e63b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e63b6-105">Parameters</span></span>  
 <span data-ttu-id="e63b6-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="e63b6-106">pRVA</span></span>  
 <span data-ttu-id="e63b6-107">określoną Wskaźnik do względnego adresu wirtualnego (RVA) pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="e63b6-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e63b6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e63b6-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e63b6-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e63b6-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e63b6-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e63b6-110">Requirements</span></span>  
 <span data-ttu-id="e63b6-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e63b6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e63b6-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e63b6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e63b6-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e63b6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e63b6-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e63b6-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63b6-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e63b6-115">See also</span></span>

- [<span data-ttu-id="e63b6-116">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="e63b6-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="e63b6-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e63b6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
