---
title: 'ICorDebugStaticFieldSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d99e06c1093dbc67e9c1999e4b9ccabd6579340e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962658"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="f1960-102">ICorDebugStaticFieldSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="f1960-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="f1960-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="f1960-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1960-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1960-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1960-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1960-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="f1960-106">określoną Wskaźnik do długości pola.</span><span class="sxs-lookup"><span data-stu-id="f1960-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1960-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1960-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1960-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f1960-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1960-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1960-109">Requirements</span></span>  
 <span data-ttu-id="f1960-110">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1960-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1960-111">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1960-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1960-112">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1960-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1960-113">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1960-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1960-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1960-114">See also</span></span>

- [<span data-ttu-id="f1960-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="f1960-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f1960-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f1960-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
