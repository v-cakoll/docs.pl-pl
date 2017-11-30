---
title: "ICorDebugExceptionDebugEvent::GetFlags — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33534a65f7a58981abd3df324b5fe005a06669d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="fea57-102">ICorDebugExceptionDebugEvent::GetFlags — metoda</span><span class="sxs-lookup"><span data-stu-id="fea57-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="fea57-103">Pobiera flagę wskazującą, czy wyjątek może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="fea57-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea57-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fea57-104">Syntax</span></span>  
  
```  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fea57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fea57-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="fea57-106">[out] Wskaźnik do [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) wartość, która wskazuje, czy wyjątek może zostać przechwycony.</span><span class="sxs-lookup"><span data-stu-id="fea57-106">[out] A pointer to a [CorDebugExceptionFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fea57-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fea57-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fea57-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fea57-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea57-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fea57-109">Requirements</span></span>  
 <span data-ttu-id="fea57-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fea57-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fea57-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fea57-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fea57-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fea57-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fea57-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea57-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea57-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fea57-114">See Also</span></span>  
 [<span data-ttu-id="fea57-115">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="fea57-115">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="fea57-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="fea57-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
