---
title: ICorDebugMemoryBuffer, interfejs
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
ms.openlocfilehash: 9e43f9a2297eb56755c7a6bba73e994441cbfeaa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127980"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="fee9d-102">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="fee9d-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="fee9d-103">Reprezentuje bufor w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fee9d-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fee9d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fee9d-104">Methods</span></span>  
  
|<span data-ttu-id="fee9d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fee9d-105">Method</span></span>|<span data-ttu-id="fee9d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fee9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fee9d-107">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="fee9d-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="fee9d-108">Pobiera rozmiar buforu pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="fee9d-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="fee9d-109">GetStartAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="fee9d-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="fee9d-110">Pobiera początkowy adres bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="fee9d-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee9d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fee9d-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fee9d-112">Ten interfejs jest dostępny tylko dla .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fee9d-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="fee9d-113">W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="fee9d-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee9d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fee9d-114">Requirements</span></span>  
 <span data-ttu-id="fee9d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee9d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee9d-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fee9d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fee9d-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fee9d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee9d-118">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee9d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee9d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fee9d-119">See also</span></span>

- [<span data-ttu-id="fee9d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fee9d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fee9d-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fee9d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
