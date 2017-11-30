---
title: "ICorDebugLoadedModule::GetBaseAddress — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b192c606697896371202e98945f83623bbb99bb9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="de0b7-102">ICorDebugLoadedModule::GetBaseAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="de0b7-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="de0b7-103">Pobiera adres podstawowy załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="de0b7-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de0b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="de0b7-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de0b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="de0b7-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="de0b7-106">[out] Wskaźnik do adres podstawowy załadować modułu.</span><span class="sxs-lookup"><span data-stu-id="de0b7-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de0b7-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="de0b7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de0b7-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="de0b7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de0b7-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de0b7-109">Requirements</span></span>  
 <span data-ttu-id="de0b7-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de0b7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de0b7-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de0b7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de0b7-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de0b7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de0b7-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de0b7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de0b7-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de0b7-114">See Also</span></span>  
 [<span data-ttu-id="de0b7-115">Icordebugloadedmodule — interfejs</span><span class="sxs-lookup"><span data-stu-id="de0b7-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="de0b7-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="de0b7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
