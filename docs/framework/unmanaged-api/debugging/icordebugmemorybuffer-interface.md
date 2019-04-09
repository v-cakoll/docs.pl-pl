---
title: ICorDebugMemoryBuffer, interfejs
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072912"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="515b1-102">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="515b1-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="515b1-103">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="515b1-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="515b1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="515b1-104">Methods</span></span>  
  
|<span data-ttu-id="515b1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="515b1-105">Method</span></span>|<span data-ttu-id="515b1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="515b1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="515b1-107">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="515b1-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="515b1-108">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="515b1-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="515b1-109">GetStartAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="515b1-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="515b1-110">Pobiera adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="515b1-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="515b1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="515b1-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="515b1-112">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="515b1-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="515b1-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="515b1-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="515b1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="515b1-114">Requirements</span></span>  
 <span data-ttu-id="515b1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="515b1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="515b1-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="515b1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="515b1-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="515b1-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="515b1-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="515b1-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="515b1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="515b1-119">See also</span></span>

- [<span data-ttu-id="515b1-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="515b1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="515b1-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="515b1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
