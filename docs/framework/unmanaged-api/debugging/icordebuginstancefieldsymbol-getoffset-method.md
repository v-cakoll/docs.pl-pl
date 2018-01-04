---
title: "ICorDebugInstanceFieldSymbol::GetOffset — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ab38a19d2bd2d06f2a04d7efafcdad6956ad7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="4a197-102">ICorDebugInstanceFieldSymbol::GetOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="4a197-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="4a197-103">Pobiera przesunięcie w bajtach tego pola wystąpienia w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4a197-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a197-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a197-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a197-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a197-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="4a197-106">Wskaźnik do liczba bajtów, że to pole wystąpienia jest przesunięta w swojej klasie nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="4a197-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a197-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a197-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a197-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4a197-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a197-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a197-109">Requirements</span></span>  
 <span data-ttu-id="4a197-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a197-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a197-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a197-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a197-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a197-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a197-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a197-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a197-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a197-114">See Also</span></span>  
 [<span data-ttu-id="4a197-115">ICorDebugInstanceFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a197-115">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="4a197-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4a197-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
