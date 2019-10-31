---
title: 'ICorDebugInstanceFieldSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 71828cd8486e2ff09190d23473dbab303b92f933
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139021"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="d7427-102">ICorDebugInstanceFieldSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="d7427-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="d7427-103">Pobiera rozmiar w bajtach pola wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d7427-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7427-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7427-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7427-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7427-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="d7427-106">określoną Wskaźnik do długości pola.</span><span class="sxs-lookup"><span data-stu-id="d7427-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7427-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7427-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7427-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d7427-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7427-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7427-109">Requirements</span></span>  
 <span data-ttu-id="d7427-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7427-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7427-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d7427-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7427-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d7427-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7427-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7427-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7427-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7427-114">See also</span></span>

- [<span data-ttu-id="d7427-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="d7427-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="d7427-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d7427-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
