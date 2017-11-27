---
title: Interfejs ICorDebugMemoryBuffer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80002d064c48a90236a64a3d0a56fab5877cf411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="0312e-102">Interfejs ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="0312e-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="0312e-103">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0312e-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0312e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0312e-104">Methods</span></span>  
  
|<span data-ttu-id="0312e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0312e-105">Method</span></span>|<span data-ttu-id="0312e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0312e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0312e-107">GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="0312e-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="0312e-108">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0312e-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="0312e-109">GetStartAddress — metoda</span><span class="sxs-lookup"><span data-stu-id="0312e-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="0312e-110">Pobiera początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="0312e-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0312e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0312e-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0312e-112">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0312e-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0312e-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0312e-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0312e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0312e-114">Requirements</span></span>  
 <span data-ttu-id="0312e-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0312e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0312e-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0312e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0312e-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0312e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0312e-118">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0312e-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0312e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0312e-119">See Also</span></span>  
 [<span data-ttu-id="0312e-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="0312e-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0312e-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0312e-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
