---
title: ICorDebugLoadedModule::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 6a1c8c94b3c45ac995501b84bb4a69d73e7db25b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209854"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="32afc-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="32afc-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="32afc-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="32afc-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32afc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32afc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32afc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32afc-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="32afc-106">określoną Wskaźnik do liczby bajtów w załadowanym module.</span><span class="sxs-lookup"><span data-stu-id="32afc-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32afc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32afc-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32afc-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="32afc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32afc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32afc-109">Requirements</span></span>  
 <span data-ttu-id="32afc-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32afc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32afc-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32afc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32afc-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="32afc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32afc-113">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32afc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32afc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32afc-114">See also</span></span>

- [<span data-ttu-id="32afc-115">ICorDebugLoadedModule — interfejs</span><span class="sxs-lookup"><span data-stu-id="32afc-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="32afc-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="32afc-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
