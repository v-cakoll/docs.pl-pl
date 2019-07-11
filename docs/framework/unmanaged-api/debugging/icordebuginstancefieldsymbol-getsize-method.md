---
title: ICorDebugInstanceFieldSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a4fdef8b5eaa99eed9605e7563110dda1b1f11f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760073"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="fc9c7-102">ICorDebugInstanceFieldSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="fc9c7-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="fc9c7-103">Pobiera rozmiar w bajtach pole wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fc9c7-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc9c7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc9c7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc9c7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc9c7-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="fc9c7-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="fc9c7-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc9c7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc9c7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc9c7-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fc9c7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc9c7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc9c7-109">Requirements</span></span>  
 <span data-ttu-id="fc9c7-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc9c7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc9c7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc9c7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc9c7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc9c7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc9c7-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc9c7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9c7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc9c7-114">See also</span></span>

- [<span data-ttu-id="fc9c7-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc9c7-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="fc9c7-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fc9c7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
