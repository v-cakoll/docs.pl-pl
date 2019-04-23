---
title: ICorDebugStaticFieldSymbol::GetSize Method
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9baa3632b6ede9ce45f34302611710344ed33761
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154326"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="6d50f-102">ICorDebugStaticFieldSymbol::GetSize Method</span><span class="sxs-lookup"><span data-stu-id="6d50f-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="6d50f-103">Pobiera rozmiar w bajtach pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="6d50f-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d50f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d50f-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d50f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d50f-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="6d50f-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="6d50f-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d50f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d50f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6d50f-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d50f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d50f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d50f-109">Requirements</span></span>  
 <span data-ttu-id="6d50f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d50f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d50f-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d50f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d50f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d50f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d50f-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d50f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d50f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d50f-114">See also</span></span>

- [<span data-ttu-id="6d50f-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d50f-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="6d50f-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d50f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
