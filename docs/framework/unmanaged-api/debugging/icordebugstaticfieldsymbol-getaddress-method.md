---
title: 'ICorDebugStaticFieldSymbol:: GetAddress — Metoda'
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: be4d59fe668026c4b40be4c6d0afcf718c8157bd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791846"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="ec0fa-102">ICorDebugStaticFieldSymbol:: GetAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec0fa-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>
<span data-ttu-id="ec0fa-103">Pobiera adres pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="ec0fa-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec0fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec0fa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec0fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec0fa-105">Parameters</span></span>  
 <span data-ttu-id="ec0fa-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="ec0fa-106">pRVA</span></span>  
 <span data-ttu-id="ec0fa-107">określoną Wskaźnik do względnego adresu wirtualnego (RVA) pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="ec0fa-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec0fa-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec0fa-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec0fa-109">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ec0fa-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec0fa-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec0fa-110">Requirements</span></span>  
 <span data-ttu-id="ec0fa-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec0fa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec0fa-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ec0fa-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec0fa-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ec0fa-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec0fa-114">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec0fa-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec0fa-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec0fa-115">See also</span></span>

- [<span data-ttu-id="ec0fa-116">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec0fa-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="ec0fa-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ec0fa-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
