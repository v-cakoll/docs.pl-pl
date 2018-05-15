---
title: Interfejs ICorDebugMemoryBuffer
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a1bc8e1206b8a82127645362cfe0a124074271c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="b064b-102">Interfejs ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="b064b-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="b064b-103">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b064b-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b064b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b064b-104">Methods</span></span>  
  
|<span data-ttu-id="b064b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b064b-105">Method</span></span>|<span data-ttu-id="b064b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b064b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b064b-107">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="b064b-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="b064b-108">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b064b-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="b064b-109">GetStartAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="b064b-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="b064b-110">Pobiera początkowy adres buforu pamięci.</span><span class="sxs-lookup"><span data-stu-id="b064b-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b064b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b064b-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b064b-112">Ten interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b064b-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b064b-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b064b-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b064b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b064b-114">Requirements</span></span>  
 <span data-ttu-id="b064b-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b064b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b064b-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b064b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b064b-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b064b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b064b-118">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b064b-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b064b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b064b-119">See Also</span></span>  
 [<span data-ttu-id="b064b-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b064b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b064b-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b064b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
