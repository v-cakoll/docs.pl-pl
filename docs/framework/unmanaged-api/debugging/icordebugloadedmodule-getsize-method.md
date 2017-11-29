---
title: "ICorDebugLoadedModule::GetSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29adc45df57c5f31c299dc28b611bcf0599d4aac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="a09e5-102">ICorDebugLoadedModule::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="a09e5-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="a09e5-103">Pobiera rozmiar w bajtach załadowanego modułu.</span><span class="sxs-lookup"><span data-stu-id="a09e5-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a09e5-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a09e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a09e5-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="a09e5-106">[out] Wskaźnik do liczba bajtów w module załadowany.</span><span class="sxs-lookup"><span data-stu-id="a09e5-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a09e5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a09e5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a09e5-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a09e5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09e5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a09e5-109">Requirements</span></span>  
 <span data-ttu-id="a09e5-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a09e5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09e5-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a09e5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a09e5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a09e5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a09e5-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09e5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09e5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a09e5-114">See Also</span></span>  
 [<span data-ttu-id="a09e5-115">Icordebugloadedmodule — interfejs</span><span class="sxs-lookup"><span data-stu-id="a09e5-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="a09e5-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="a09e5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
