---
title: "ICorDebugStaticFieldSymbol::GetSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 256a15952cd52c5a096e1f0b8c7fc2086cde226c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="a53a6-102">ICorDebugStaticFieldSymbol::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="a53a6-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="a53a6-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="a53a6-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a53a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a53a6-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a53a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a53a6-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="a53a6-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="a53a6-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a53a6-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a53a6-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a53a6-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a53a6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a53a6-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a53a6-109">Requirements</span></span>  
 <span data-ttu-id="a53a6-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a53a6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a53a6-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a53a6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a53a6-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a53a6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a53a6-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a53a6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a53a6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a53a6-114">See Also</span></span>  
 [<span data-ttu-id="a53a6-115">Interfejs ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="a53a6-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="a53a6-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="a53a6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
