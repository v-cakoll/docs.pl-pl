---
title: ICorDebugStaticFieldSymbol::GetAddress Method
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e233fe78f6b2c721114f0307a8ca414625a0087e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160423"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="6f673-102">ICorDebugStaticFieldSymbol::GetAddress Method</span><span class="sxs-lookup"><span data-stu-id="6f673-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="6f673-103">Pobiera adres pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="6f673-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f673-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6f673-104">Syntax</span></span>  
  
```  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f673-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f673-105">Parameters</span></span>  
 <span data-ttu-id="6f673-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="6f673-106">pRVA</span></span>  
 <span data-ttu-id="6f673-107">[out] Wskaźnik do wirtualnej adres względny (RVA) pole statyczne.</span><span class="sxs-lookup"><span data-stu-id="6f673-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f673-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f673-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f673-109">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6f673-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f673-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6f673-110">Requirements</span></span>  
 <span data-ttu-id="6f673-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f673-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f673-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f673-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f673-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f673-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f673-114">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f673-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f673-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f673-115">See also</span></span>

- [<span data-ttu-id="6f673-116">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="6f673-116">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="6f673-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6f673-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
