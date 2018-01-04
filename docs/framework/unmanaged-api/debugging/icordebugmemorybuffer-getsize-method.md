---
title: "ICorDebugMemoryBuffer::GetSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658fb2ce289b4b8cabfcf0cc2ea5f8dace2ec754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="af5f5-102">ICorDebugMemoryBuffer::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="af5f5-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="af5f5-103">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="af5f5-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af5f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="af5f5-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af5f5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="af5f5-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="af5f5-106">[out] Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="af5f5-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af5f5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af5f5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af5f5-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="af5f5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af5f5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af5f5-109">Requirements</span></span>  
 <span data-ttu-id="af5f5-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af5f5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af5f5-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af5f5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af5f5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af5f5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af5f5-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af5f5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5f5-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af5f5-114">See Also</span></span>  
 [<span data-ttu-id="af5f5-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="af5f5-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="af5f5-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="af5f5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
