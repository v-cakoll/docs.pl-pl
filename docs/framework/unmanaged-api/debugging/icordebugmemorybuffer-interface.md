---
title: ICorDebugMemoryBuffer, interfejs
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072912"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="b8d6c-102">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="b8d6c-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="b8d6c-103">Reprezentuje buforów w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8d6c-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b8d6c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b8d6c-104">Methods</span></span>  
  
|<span data-ttu-id="b8d6c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b8d6c-105">Method</span></span>|<span data-ttu-id="b8d6c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b8d6c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b8d6c-107">GetSize, metoda</span><span class="sxs-lookup"><span data-stu-id="b8d6c-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="b8d6c-108">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b8d6c-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="b8d6c-109">GetStartAddress, metoda</span><span class="sxs-lookup"><span data-stu-id="b8d6c-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="b8d6c-110">Pobiera adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8d6c-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8d6c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b8d6c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d6c-112">Ten interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b8d6c-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="b8d6c-113">W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="b8d6c-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8d6c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b8d6c-114">Requirements</span></span>  
 <span data-ttu-id="b8d6c-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8d6c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8d6c-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8d6c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8d6c-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8d6c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8d6c-118">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8d6c-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d6c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8d6c-119">See also</span></span>

- [<span data-ttu-id="b8d6c-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b8d6c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b8d6c-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b8d6c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
