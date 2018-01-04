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
ms.workload: dotnet
ms.openlocfilehash: 98703b07f6601307b5f26aa14b2faf67f8823be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="41adb-102">Interfejs ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="41adb-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="41adb-103">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="41adb-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41adb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41adb-104">Methods</span></span>  
  
|<span data-ttu-id="41adb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41adb-105">Method</span></span>|<span data-ttu-id="41adb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41adb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41adb-107">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="41adb-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="41adb-108">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="41adb-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="41adb-109">GetStartAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="41adb-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="41adb-110">Pobiera początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="41adb-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41adb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41adb-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41adb-112">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="41adb-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="41adb-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="41adb-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41adb-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41adb-114">Requirements</span></span>  
 <span data-ttu-id="41adb-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41adb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41adb-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41adb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41adb-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41adb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41adb-118">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41adb-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41adb-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41adb-119">See Also</span></span>  
 [<span data-ttu-id="41adb-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="41adb-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="41adb-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="41adb-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
