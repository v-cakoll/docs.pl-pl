---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: f207cd1c612b6444a9512adaa356ac2d01de7b9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788467"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="b2421-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="b2421-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="b2421-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="b2421-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2421-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2421-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2421-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b2421-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="b2421-106">określoną Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="b2421-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2421-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2421-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2421-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b2421-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2421-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2421-109">Requirements</span></span>  
 <span data-ttu-id="b2421-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2421-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2421-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2421-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2421-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2421-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2421-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2421-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2421-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2421-114">See also</span></span>

- [<span data-ttu-id="b2421-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="b2421-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="b2421-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2421-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
