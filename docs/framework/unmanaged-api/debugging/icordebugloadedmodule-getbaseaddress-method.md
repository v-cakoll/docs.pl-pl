---
title: ICorDebugLoadedModule::GetBaseAddress — metoda
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 190c9114cffa537ba162b19abdf30d5a6aee87f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788443"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="ff8b0-102">ICorDebugLoadedModule::GetBaseAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="ff8b0-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="ff8b0-103">Pobiera adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="ff8b0-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8b0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ff8b0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff8b0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ff8b0-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="ff8b0-106">określoną Wskaźnik na adres podstawowy załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="ff8b0-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff8b0-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ff8b0-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff8b0-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ff8b0-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff8b0-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ff8b0-109">Requirements</span></span>  
 <span data-ttu-id="ff8b0-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff8b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff8b0-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ff8b0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ff8b0-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ff8b0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff8b0-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff8b0-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8b0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff8b0-114">See also</span></span>

- [<span data-ttu-id="ff8b0-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="ff8b0-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ff8b0-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ff8b0-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
