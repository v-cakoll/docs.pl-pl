---
title: 'ICorDebugStaticFieldSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: 0fa9c519a40624dd8c5471231263d2430738af87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131769"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="7acc3-102">ICorDebugStaticFieldSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="7acc3-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="7acc3-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="7acc3-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7acc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7acc3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7acc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7acc3-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="7acc3-106">określoną Wskaźnik do długości pola.</span><span class="sxs-lookup"><span data-stu-id="7acc3-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7acc3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7acc3-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7acc3-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7acc3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7acc3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7acc3-109">Requirements</span></span>  
 <span data-ttu-id="7acc3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7acc3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7acc3-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7acc3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7acc3-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7acc3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7acc3-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7acc3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7acc3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7acc3-114">See also</span></span>

- [<span data-ttu-id="7acc3-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="7acc3-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="7acc3-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7acc3-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
