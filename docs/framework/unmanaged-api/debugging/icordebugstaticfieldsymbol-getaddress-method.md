---
title: ICorDebugStaticFieldSymbol::GetAddress Method
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a78df94fdc4190a43c80b0a8e3457f164e38eb00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498058"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="f8584-102">ICorDebugStaticFieldSymbol::GetAddress Method</span><span class="sxs-lookup"><span data-stu-id="f8584-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="f8584-103">Pobiera adres pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="f8584-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8584-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8584-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8584-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8584-105">Parameters</span></span>  
 <span data-ttu-id="f8584-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="f8584-106">pRVA</span></span>  
 <span data-ttu-id="f8584-107">[out] Wskaźnik do wirtualnej adres względny (RVA) pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="f8584-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8584-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8584-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8584-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f8584-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8584-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8584-110">Requirements</span></span>  
 <span data-ttu-id="f8584-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8584-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8584-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8584-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8584-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8584-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8584-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8584-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8584-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8584-115">See also</span></span>
- [<span data-ttu-id="f8584-116">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8584-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="f8584-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f8584-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
