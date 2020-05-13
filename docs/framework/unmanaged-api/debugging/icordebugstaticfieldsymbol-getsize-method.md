---
title: 'ICorDebugStaticFieldSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: e36c94bf411e75f915cca86aee74cdf161674d25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379413"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="5a3f4-102">ICorDebugStaticFieldSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="5a3f4-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="5a3f4-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="5a3f4-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a3f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a3f4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a3f4-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="5a3f4-106">określoną Wskaźnik do długości pola.</span><span class="sxs-lookup"><span data-stu-id="5a3f4-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a3f4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a3f4-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a3f4-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5a3f4-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a3f4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a3f4-109">Requirements</span></span>  
 <span data-ttu-id="5a3f4-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a3f4-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a3f4-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5a3f4-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a3f4-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5a3f4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a3f4-113">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a3f4-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a3f4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a3f4-114">See also</span></span>

- [<span data-ttu-id="5a3f4-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a3f4-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="5a3f4-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5a3f4-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
