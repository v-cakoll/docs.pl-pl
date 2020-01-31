---
title: 'ICorDebugStaticFieldSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: deeb887dad38417e3ebb980f5ef2f89392388d65
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791817"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="09124-102">ICorDebugStaticFieldSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="09124-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="09124-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="09124-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09124-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09124-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09124-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09124-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="09124-106">określoną Wskaźnik do długości pola.</span><span class="sxs-lookup"><span data-stu-id="09124-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09124-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09124-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09124-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09124-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09124-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09124-109">Requirements</span></span>  
 <span data-ttu-id="09124-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09124-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09124-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09124-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09124-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09124-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09124-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09124-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09124-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09124-114">See also</span></span>

- [<span data-ttu-id="09124-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="09124-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="09124-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="09124-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
