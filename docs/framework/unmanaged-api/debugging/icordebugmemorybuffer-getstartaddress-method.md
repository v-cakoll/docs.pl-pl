---
title: "ICorDebugMemoryBuffer::GetStartAddress — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 97c08e87f63b36bfee5ade75e44f4867441bee92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="a528f-102">ICorDebugMemoryBuffer::GetStartAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="a528f-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="a528f-103">Pobiera początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="a528f-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a528f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a528f-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a528f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a528f-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="a528f-106">[out] Wskaźnik do początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="a528f-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a528f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a528f-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="a528f-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a528f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a528f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a528f-109">Requirements</span></span>  
 <span data-ttu-id="a528f-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a528f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a528f-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a528f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a528f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a528f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a528f-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a528f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a528f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a528f-114">See Also</span></span>  
 [<span data-ttu-id="a528f-115">Interfejs ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="a528f-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="a528f-116">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="a528f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
