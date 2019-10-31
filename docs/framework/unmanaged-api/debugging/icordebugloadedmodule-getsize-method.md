---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 3f2f8a1721847b8f7b845c42aa3c91e032c2d474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122644"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="ef6be-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="ef6be-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="ef6be-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="ef6be-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef6be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef6be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef6be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef6be-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="ef6be-106">określoną Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="ef6be-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef6be-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef6be-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef6be-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ef6be-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef6be-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef6be-109">Requirements</span></span>  
 <span data-ttu-id="ef6be-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef6be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef6be-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ef6be-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef6be-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ef6be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef6be-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef6be-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6be-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef6be-114">See also</span></span>

- [<span data-ttu-id="ef6be-115">ICorDebugLoadedModule, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef6be-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ef6be-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ef6be-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
